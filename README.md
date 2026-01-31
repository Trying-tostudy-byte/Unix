# Unix
Navigation and Directory Management
• pwd (Present Working Directory): Executed to confirm the user's current location in the file system.
• ls (List): Used to view directory contents. Variations included ls -l for long-format listings showing file metadata and ls [directory name] to view a folder's contents remotely.
• cd (Change Directory): Run to move into specific folders (e.g., cd demo_1) or back to the parent directory using cd ...
• mkdir (Make Directory): Used to create new folders such as demo_1 and test-project.
• mkdir -p: A specific flag used to create parent and subdirectories simultaneously, such as building a project structure like genomics-project/data/sequence in one step.
File Creation and Manipulation
• touch: Run to create empty files, notably used with brace expansion to generate multiple sequencing files at once, such as sample_{A,B,C}_R{1,2}.fastq.
• cp (Copy): Executed to duplicate files. The instructor demonstrated using the -t (target) flag to specify the destination directory.
• mv (Move/Rename): Used both to move files between directories and to rename folders, such as changing demo_3 to test.
• rmdir (Remove Directory): Run to delete empty directories.
• rm -rf: Used to forcefully and recursively delete directories that contain files.

commands:
1. Directory & File Creation
mkdir demo
mkdir demo_1
touch demo.csv
touch random.tsv
2. Viewing Files
cat random.tsv
3. Writing to Files
echo "Hello World" > random.tsv
echo "Second Line" >> random.tsv
Standard Streams and Redirection
• echo: Used to output strings.
    ◦ > (Overwrite): Redirects output to a file, replacing any existing content.
    ◦ >> (Append): Redirects output to a file by concatenating it to the end of the existing text.


Lecture 2 — Shell Expansion & Automation

1. Shell Expansion (Wildcards) Used to automate repetitive tasks.
echo languages{Python,R,Rust}
Output:
languagesPython languagesR languagesRust

2. Creating Multiple Directories at Once
mkdir -p genomics_project/{data/{sequence},script,analysis}

3. Creating Multiple Files (FASTQ example)
touch sample{A,B,C}_R{1,2}.fastq
Creates:
sampleA_R1.fastq sampleA_R2.fastq
sampleB_R1.fastq sampleB_R2.fastq
sampleC_R1.fastq sampleC_R2.fastq

4. Wildcards: Matches similar patterns (e.g., ls sequence/sample_B* fetches all files for Sample B)
   
5.. Square Brackets []: Matches specific character ranges (e.g., ls sequence/sample_[A-C]_R2.fastq)
   
6. Standard Error Redirection 2>: Separates error messages from successful output.
    ◦ Example: ls -l file1 file2 > output.txt 2> error.log saves the file list to one file and any "file not found" errors to another
   
7. Piping |: Creates a pipeline by feeding the output of one command as input to the next
8. grep: Search tool for pattern matching.
    ◦ grep -v ">" tb1.fasta: Invert matching to ignore FASTA headers.
    ◦ grep --color "[^ATGC]": Highlights non-nucleotide characters (mismatches)
9. Flags
   -p : Create parent directories if missing

Lecture 3: Data Inspection and Text Processing
Specialised tools were used to examine biological data formats like GTF and FASTA.
1. less: A terminal page reader used to scroll through large files without loading the entire file into RAM
2. Head command
   ◦ head filename - first 10 lines of a file
   ◦ head -n 20 tb1.fasta - first 20 lines of the file
3. Tail: tail -n 20 filename - last 20 lines of the file
4. grep -c: Counts the number of occurrences of a pattern (e.g., counting the number of reads/headers
5. grep -o: Prints only the matching part of the string rather than the whole line
6. wc (Word Count):
    ◦ wc -l: Counts the number of lines.
    ◦ wc -m: Counts the number of characters (used to count DNA bases).
    ◦ wc -w: Counts the number of words

Session 4: Version Control with Git and GitHub
These commands manage code changes, snapshots, and collaboration.
1. git config --global user.name/email: Identifies the user to the Git system.
   git config --global user.name "Tahreem Shaikh"
   git config --global user.email "tahreemshaikh02@gmail.com"
3. ssh-keygen: Generates a secure key to allow the terminal to communicate with GitHub.
   ssh-keygen -t rsa -b 4096 -C "tahreemshaikh03@gmail.com"
5. git init: Initializes a new local Git repository to start tracking changes.
6. git status: Shows the state of the repository, including tracked, untracked, and modified files.
7. git add [file]: Moves a file to the staging area, indicating it is ready to be committed.
8. git commit -m "[message]": Takes a snapshot (commit) of the project with a descriptive message.
9. git log: Displays the history of all snapshots taken.
10. git diff: Shows the exact difference (added or deleted lines) between the current file and the last commit.
11. git restore [file]: Undoes recent changes to a file to go back to the previous version.
12. git restore --staged [file]: Unstages a file that was accidentally added.
13. git rm / git mv: Used to remove or rename files while maintaining the Git tracking history.
14. git remote add origin https://github.com/Trying-tostudy-byte/Unix/ : Links a local repository to a remote repository on GitHub.
15. git push origin [branch]: Uploads local commits to the GitHub server.
16. git pull origin [branch]: Downloads changes from the remote server to the local machine.
17. git clone [URL]: Creates a local copy of an existing remote GitHub repository
