# Activity 1

### Create 20 files with .txt extensions and rename the first 5 files to .yml extension Print the latest created top 5 files among the total no of files

```bash
# Changing to root user
sudo su

# Creating a new Directory called guvi in desktop Directory
cd Desktop/
mkdir guvi

# Creating 20 txt files in a single command
touch file{1..20}.txt

# To list newly created all files
ls

# Rename First 5 files to .yml extension
mv file1.txt file1.yml
mv file2.txt file2.yml
mv file3.txt file3.yml
mv file4.txt file4.yml
mv file5.txt file5.yml

# To Print latest created top 5 files
ls -lt | head -n 6
```
