********************************
Git
********************************

Remove commit history based on certain file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

  Remove
  git filter-branch --force --index-filter "git rm --cached --ignore-unmatch path/to/local/file" --prune-empty --tag-name-filter cat -- --all
  git push --force --verbose --dry-run
  git push --force