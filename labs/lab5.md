Today
Review
Permissions
Conda environments
Running Fastqc
Redirection (if there is time)
:::::::::::::::::::::::::::::::::::::::: keypoints

You can view file permissions using ls -l and change permissions using chmod.
The history command and the up arrow on your keyboard can be used to repeat recently used commands.
Conda environments simplify reporducability, dependencies and sharing environments.
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: review

You can view file contents using less, cat, head or tail.
head- should the top portion of the file text
tail- shows bottom text of file
cat- moved file content to the directory
less- makes easy to scroll through file

The commands cp, mv, and mkdir are useful for manipulating existing files and creating new directories.
cp- copy
mv- move mv directory/oldname directory/newname (directory name is not needed if working within the directory)
mkdir- make new directory

Quality scores. Highest score for a base is 41
Quality encoding: !"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJ 
| | | | | 
Quality score: 01........11........21........31........41

::::::::::::::::::::::::::::::::::::::::::::::::::

*Warm ups: What is the last read in the SRR2584863_1.fastq file? How confident are you in this read?
Dont have this file

l A: 

How big are your fastqs? (Hint: Look at the options for the ls command to see how to show file sizes.)

ls -l -h 
-rw-r--r--. 1 mry1011 domain users 47K Feb 13 16:49 SRR097977-backup.fastq
-rw-r--r--. 1 mry1011 domain users 47K Jan 30 10:53 SRR097977.fastq
-rw-r--r--. 1 mry1011 domain users 43K Feb 13 16:49 SRR098026.fastq

hint, it involves 'ls'. See if you can do it using a relative and absolute path
another hint: There is an option to make it easy to read the file size. Use one of the two methods to find it A:
EXERCISE 5.1
Starting in the shell_data/untrimmed_fastq directory, do the following:

Make sure that you have deleted your backup directory and all files it contains. Create a backup of each of your FASTQ files using cp. (Note: You’ll need to do this individually for each of the two FASTQ files. We haven’t learned yet how to do this with a wildcard.) Use a wildcard to move all of your backup files to a new backup directory. Paste the code you used to do each step between the ''' below:

rm -Rf backup/
mkdir backup
cp SRR097977.fastq backup/SRR097977-backup.fastq
cp SRR098026.fastq backup/SRR098026-backup.fastq

longhand: cp SRR098026.fastq /home/users/mry1011/gen711-811/shell_data/backup/SRR097977-backup.fastq
shorthand: cp SRR097977.fastq backup/SRR097977-backup.fastq

wildcard option: *.fastq 

File Permissions Help
The first part of the output for the -l flag gives you information about the file's current permissions. There are ten slots in the permissions list. The first character in this list is related to file type, not permissions, so we'll ignore it for now. The next three characters relate to the permissions that the file owner has, the next three relate to the permissions for group members, and the final three characters specify what other users outside of your group can do with the file. We're going to concentrate on the three positions that deal with your permissions (as the file owner).

should look like: -rw-r--r--

{alt='Permissions breakdown'}

Here the three positions that relate to the file owner are rw-. The r means that you have permission to read the file, the w indicates that you have permission to write to (i.e. make changes to) the file, and the third position is a -, indicating that you don't have permission to carry out the ability encoded by that space (this is the space where x or executable ability is stored, we'll talk more about this later).

chmod ug+rwx meaning change the modification permissions of users and group to read, write, not last thing
chmod g-xwx meaning change modification permissions of group to exclude writing

EXERCISE 5.2
Change the permissions on all of your backup files to be write-protected.

chmod ug+rwx SRR098026-backup.fastq

How do you know they are write protected? A:

EXERCISE 5.3: CONDA ENVIRONMENTS AND PROGRAMS

conda activate genomics
conda deactivate

After loading a conda environment, where is the program 'fastqc' stored?

-h for help
fastqc *.fastq*

Explore the fastqc output. Which samples failed at least one of FastQC’s quality tests? What test(s) did those samples fail?
:::::::::::::::::::::::::::::::::::::::: keypoints

Use which for commands/programs to see where they are installed
You can view file permissions using ls -l and change permissions using chmod.
The history command and the up arrow on your keyboard can be used to repeat recently used commands.
Explain what a conda environment is, and how to activate and deactivate it
::::::::::::::::::::::::::::::::::::::::::::::::::