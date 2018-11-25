Git and Bash commands
=====

`git log -S [SEARCH-PARAMETER] -p`

This will search your commit history for a file with the search parameter, and then show you the file’s contents in the terminal.
#  

`git filter-branch --force --index-filter \ ‘git rm --cached --ignore-unmatch [PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA] \ --prune-empty --tag-name-filter cat -- --all`

This will go through your entire commit history, remove the specified file and its commits, and overwrite your tags. Here’s the specific GitHub post with the actual steps: https://help.github.com/articles/removing-sensitive-data-from-a-repository/
#  

`history`

This will display a scrollable history of all the comamnds you've entered into your terminal so far.
#  

`Ctrl-R`

Entering this keyboard shortcut inside your terminal window will allow you to quickly search through your terminal history. Very handy if you're looking for a very old command you entered into terminal.