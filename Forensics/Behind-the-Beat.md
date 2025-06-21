**Difficulty: Very Easy**

Description: Agents intercepted an audio file named message.mp3. It plays a single tone, but we have intel that a flag might be tucked away in the metadata fields of the file. Can you inspect the file and uncover the flag?

# Methodology
1. Download the file.
2. Download a file analyzer. I'm using [Exiftool](https://exiftool.org/), a quick and easy-to-use command-line tool for reading file metadata.
3. Go to your terminal and run this command: `exiftool message.mp3` (or the equivalent command for your file analyzer). I ran 'exiftool /home/[user]/Downloads/message.mp3' so it can locate my file easier.
   - Tip: To find the flag faster, use `grep` to search the results for the flag. `exiftool message.mp3 | grep C1{` would run the results of the first command through the second and output only the flag.

> **Flag:** C1{metadata_tells_more}

![Screenshot 2025-06-21 at 10 16 15 AM](https://github.com/user-attachments/assets/fc00e6be-2aeb-4aa4-9612-a30b86177875)
