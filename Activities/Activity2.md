# Activity 2

### Create a file with .txt extension (/home/demo.txt). Change the permission set if that file, so that any user can read it, group can read/write & owner can read/write/execute it.

```bash
# Creating a home directory
mkdir home

# Creating a demo.txt file inside home directory
touch demo.txt

# Checking the permession of demo.txt
ls -l

# Changing the permession so that any user can read it, group can read/write & owner can read/write/execute it.
chmod 764 demo.txt

```
