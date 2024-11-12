# My Learn to Cloud Journey

## Current Progress: Phase 1 - Linux and Bash

I'm currently working through the Learn to Cloud challenge, focusing on mastering Linux and Bash fundamentals. This repository tracks my progress and contains my solutions and notes.

### Topic 1: Linux

- Read the book _Linux Basics for Hackers_ up to Chapter 9.
- Completed several challenges from the book.

### Topic 2: Version Control

- Revised the concepts due to previous experience.

### Topic 3: Infrastructure as Code

- Learned the basics of Infrastructure as Code with a focus on Terraform.
- Completed a crash course on Terraform from YouTube.

### CTF Challenge

The CTF lab included 7 challenges that tested my understanding of different Linux commands. Below are the challenges and their solutions:

#### Challenge 1: Find the hidden file in this directory and read its contents.

To find hidden files, I used the following command:

```bash
ls -a
```

Files starting with a `.` are considered hidden. This helped me locate the file.

![Answer of the first challenge](./images/challenges/challenge_1_answer.png)

#### Challenge 2: Locate the file with the word "secret" in its name anywhere in the /home/ec2-user directory.

To search for a file containing "secret" in its name, I used `grep`:

```bash
grep -r "secret" /home/ec2-user
```

- `-r` flag makes `grep` search recursively through the directory and its subdirectories.

![Answer of the second challenge](./images/challenges/challenge_2_answer.png)

#### Challenge 3: Find the largest file in the /var/log directory and retrieve the flag from it.

To find the largest file, I used `du` and `sort`:

```bash
cd /var/log
du -ah | sort -rh | head -n 1
```

- `du -ah`: Shows file sizes in human-readable format and includes all files.
- `sort -rh`: Sorts the output in reverse order by size.

The largest file found was:

```
103M ./journal/ef2474362b044445a8b8f140ffa04be6/system@ac627375d83c410193030948afab916e-000000000003e789-000626bae3dc34f6.journal
```

To retrieve the flag:

```bash
grep -r "flag" ./journal
```

![Answer of the third challenge](./images/challenges/challenge_3_answer.png)

#### Challenge 4: Identify the user with UID 1001 and find the flag in their home directory.

UIDs are stored in the `/etc/passwd` file. To locate a user with UID 1001:

```bash
grep ":1001:" /etc/passwd
```

Then, to access the user’s home directory:

```bash
sudo chmod o=rx /home/ctf_user
cd /home/ctf_user
cat flag.txt
```

![Answer of the fourth challenge](./images/challenges/challenge_4_answer.png)

#### Challenge 5: Locate the file owned by root with permissions 777 and read its contents.

I used `find` to locate files with specific permissions:

```bash
sudo find / -type f -perm 777 -exec ls -l {} +
```

- `-type f`: Search for files only.
- `-perm 777`: Search for files with permissions `777`.
- `-exec ls -l {}`: Lists detailed information about the found files.

![Answer of the fifth challenge](./images/challenges/challenge_5_answer.png)
![Answer of the fifth challenge](./images/challenges/challenge_5_final_ans.png)

#### Challenge 6: Find the process running on port 8080 and retrieve the flag from its command.

I couldn’t solve this challenge.

#### Challenge 7: Decode the base64 encoded flag in the 'encoded_flag.txt' file.

To decode the file:

```bash
cat encoded_flag.txt | base64 -d
```

- `-d` flag is used for decoding.

![Answer of the seventh challenge](./images/challenges/challenge_7_answer.png)

## Resources

I'm following the curriculum outlined at [learntocloud.guide](https://learntocloud.guide).

## Goals

- Gain proficiency in Linux command-line operations.
- Understand and effectively use Git for version control.
- Build a solid foundation for cloud computing concepts.

I'm excited to continue this journey and look forward to progressing through all phases of the Learn to Cloud challenge!

---

_This README will be updated as I progress through the challenge._
