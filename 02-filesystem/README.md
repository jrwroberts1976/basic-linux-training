Part 2 – Working with Files and Directories
---

# Working with Files and Directories

Now that you know how to move around the Linux filesystem, the next step is learning how to create, copy, move and remove files and directories.

These are some of the commands you will use every day as a Linux administrator.

---

# Creating Directories

The `mkdir` command creates a new directory.

Syntax:

```bash
mkdir directory_name

Example:

mkdir training

Verify it exists:

ls

Output:

training
Creating Multiple Directories

You can create several directories at once.

mkdir docs scripts backups

Output:

docs
scripts
backups
Creating Nested Directories

Normally Linux expects parent directories to already exist.

Using the -p option creates the entire directory structure.

mkdir -p projects/linux/module01

This creates:

projects
└── linux
    └── module01
Creating Files

Linux uses the touch command to create empty files.

touch notes.txt

Verify:

ls

Output:

notes.txt

Multiple files can be created at once.

touch file1.txt file2.txt file3.txt
Copying Files

The cp command copies files.

Syntax:

cp source destination

Example:

cp notes.txt backup.txt

Result:

notes.txt
backup.txt

The original file remains unchanged.

Copying Directories

To copy directories use:

cp -r projects backup

The -r option means recursive.

Moving Files

The mv command moves files or directories.

Example:

mv notes.txt Documents/

The file now exists in the Documents directory.

Renaming Files

The same command can rename files.

Example:

mv notes.txt lesson-notes.txt

The file has simply changed name.

Removing Files

Delete a file using:

rm filename

Example:

rm backup.txt

Once removed, the file cannot normally be recovered.

Always check before pressing Enter.

Removing Directories

Empty directories can be removed using:

rmdir directory_name

Example:

rmdir training
Removing Directories and Contents

To remove everything inside a directory:

rm -r directory_name

Example:

rm -r old-project

Be careful with this command.

The Dangerous Command

One of the most dangerous Linux commands is:

rm -rf

Where:

-r = recursive
-f = force

Example:

rm -rf test-directory

This deletes everything without asking for confirmation.

⚠️ Never run commands unless you understand exactly what they do.

Wildcards

Wildcards allow commands to work with multiple files.

Example:

rm *.txt

Deletes every file ending in .txt.

Another example:

ls *.log

Lists every log file.

Useful Keyboard Shortcuts
Shortcut	Description
↑	Previous command
↓	Next command
Tab	Auto-complete command or filename
Ctrl + C	Cancel current command
Ctrl + L	Clear the terminal
Ctrl + D	Logout / End shell
Best Practices

✔ Check your location with pwd.

✔ List files before deleting them.

✔ Use cp before making important changes.

✔ Avoid using rm -rf unless absolutely necessary.

✔ Use meaningful filenames.

✔ Organise work into directories.

Summary

You should now be able to:

Create directories
Create files
Copy files
Move files
Rename files
Delete files safely
Remove directories
Use wildcards
Use common keyboard shortcuts

In Part 3, you'll learn how to view file contents, search for help and use the Linux manual system.


---

## After this

Module 01 will be about **75% complete**.

Part 3 is where it starts feeling like a real Linux administration course. We'll cover:

- `cat`
- `less`
- `more`
- `head`
- `tail`
- `history`
- `man`
- `whatis`
- `which`
- `echo`
- Output redirection (`>`, `>>`)
- Pipes (`|`) — introduced gently, with more depth in a later module

By the end of Module 01, learners will have enough command-line knowledge to work confidently in a Linux
