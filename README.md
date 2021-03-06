## Conversion

First extraction from Mediawiki to a single .XML file (containing the current revision of all pages) was performed using the `dumpgenerator.py` tool in the `WikiTeam/wikiteam` repository:

``` python dumpgenerator.py --api=https://wiki.multitheftauto.com/api.php --xml --images --curonly ```

The extraction was made possible by using a variant of the `philipashlock/mediawiki-to-markdown` tool: this script was modified to dump all contents of the Mediawiki .XML export to separate files and directories.

Files and directories were then manually pruned to retain core documentation and remove any third-party or unrelated documentation.

After conversion to separate files and directories, the following rules were applied to each (Mediawiki syntax) file (all below commands assume OS X):

* Spaces converted to underscore (_).
* Back slashes (\) converted to forward slashes (/).
* All links appended with .md extension.
* Conversion of <code>[...]</code> into <syntaxhighlight lang="..."></syntaxhighlight> which is understood by Pandoc:

    ```
    find . -type f -name "*.wiki" -exec perl -p -i -e 's/<code>\[([a-zA-Z]+),?.*\]/<syntaxhighlight lang="\1">/g' {} \;
    find . -type f -name "*.wiki" -exec perl -p -i -e 's/<code>/<syntaxhighlight>/g' {} \;
    find . -type f -name "*.wiki" -exec perl -p -i -e 's/<\/code>/<\/syntaxhighlight>/g' {} \;
    ```

* Removal of any Mediawiki commands:
  ```
  find . -type f -name "*.wiki" -exec perl -p -i -e 's/__(NOTOC|TOC|NOEDITSECTION)__//g' {} \;
  ```

* Filename conversion to lowercase:

  ```
  for file in $(git ls-files); do git mv -f $file `echo $file | tr "[:upper:]" "[:lower:]"`; done
  ```

Remove any useless pages:

```
find . -type f -name "*.wiki" -exec grep -q -i '#REDIRECT' {} \; -exec rm {} \;
find . -type f -name "*.wiki" -exec grep -q -i '{Delete}' {} \; -exec rm {} \;
```

Conversion to Markdown (Github style) was then performed using Pandoc:

```
find . -type d -print0 >../dirs.txt
xargs -0 mkdir -p <../dirs.txt

find . -type f -name "*.wiki" -exec sh -c 'pandoc -s -S -f mediawiki -t markdown_github "${0}" -o "../md/${0%.wiki}.md"' {} \;

pandoc -s -S -f mediawiki -t markdown_github test.wiki -o test.md
```

After conversion to Markdown, perform various steps to clean up:

* Conversion of image links to proper image tags, all lowercase:

  ```
  find . -type f -name "*.md" -exec perl -p -i -e 's/\[Image:(.*?)\]\(\/(?:docs\/)?image:(.*?)\.md(.*?)\)/\!\[$1\]\(\/images\/\L$2\E\)/gi' {} \;
  ```


## Current known issues and TODOs

* Any {{...}} specific Mediawiki tags are lost. This includes the "FROM VERSION 1.5.3 ONWARDS" tags, which are _not_ shown, requiring a documentation update at a later point in time.
* Mediawiki specific pages or blobs such as File:, Template:, User:, Talk:, etc. are purged.
* Convert old Category and Template pages into index.
* Various conversion artifacts that can really only solved by hand.
