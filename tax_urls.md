Here's a sticky wickett.

cat 1
 - cat 1a
 - cat 1b
 - cat 1c
cat 2
 - cat 2a
 - cat 2b
   - cat 21a
   - cat 21b

URL paths are to be:
/products/cat1/cat1a/title/
/products/cat2/cat2a/cat21b/title/

First, you need Entity API and Entity Tokens
Trailing Backslash also (not my idea)

URL Settings
admin/config/search/path/settings/
Check reduce strings to letters and numbers
In the Puncuation select No Action for Slash (/)

URL Patterns
product/[node:[FIELD]:parents:join-path]/[node:title]/
The rub here is parents:join-path

Here's another one:

Tax relative URL
[node:field-cat-id:0:url:relative]/[node:title]
