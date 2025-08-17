1. mkdir → Make Directory

Creates a new folder (directory).

Example:

mkdir test


→ makes a folder named test.

2. rmdir → Remove Directory (empty only)

Deletes a folder, but only if it’s empty.

Example:

rmdir test


→ removes test folder if it has no files inside.

3. rm → Remove Files or Folders

Deletes files and folders (even if not empty).

Common options:

rm file.txt → removes file.

rm -r foldername → removes a folder and everything inside it.

rm -rf foldername → force remove (no questions asked). ⚠️ Dangerous, be careful!

4. mkdir -p → Make Parent Directories

Creates a folder along with its parent folders if they don’t exist.

Example:

mkdir -p a/b/c


→ makes folder a, inside it b, inside that c (all in one command).

In simple words:

mkdir = make folder

rmdir = remove empty folder

rm = remove files or folders (even if not empty)

mkdir -p = make nested folders at once
