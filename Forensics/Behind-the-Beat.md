Description: Agents intercepted an audio file named message.mp3. It plays a single tone, but we have intel that a flag might be tucked away in the metadata fields of the file. Can you inspect the file and uncover the flag?


Method: We analyzed an MP3 file suspected of containing hidden data. Using ExifTool, we discovered a flag
embedded in the file's metadata, specifically in one of the ID3 tag fields. This showed how forensic
data can often be concealed in plain sight through file attributes.

Flag: C1{metadata_tells_more}

![Screenshot 2025-06-21 at 10 16 15 AM](https://github.com/user-attachments/assets/fc00e6be-2aeb-4aa4-9612-a30b86177875)
