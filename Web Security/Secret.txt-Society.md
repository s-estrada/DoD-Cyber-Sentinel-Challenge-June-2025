**Difficulty: Very Easy**

_Description:_ Our team suspects that a Juche Jaguar developer accidentally left something interesting behind on a public site: https://juche.msoidentity.com. You’ve been tasked with examining its structure. Can you uncover what the bots were told to ignore? Start with the usual entry points a crawler might explore. One disallowed path leads to a page where someone left behind more than just code.

# Tools Used
**curl:** A command-line tool used for transferring data with URLs, essential for fetching web content and inspecting page sources.

**Gobuster:** A command-line tool designed for brute-forcing to discover hidden directories, files, and other resources on web servers and websites, as well as DNS subdomains and virtual hosts. 

# Methodology
1. Examine robots.txt for Disallowed Paths: My first step was to check the robots.txt file, a common initial point for web crawlers, for any hidden directories. I used the command 'curl https://juche.msoidentity.com/robots.txt' to retrieve its contents. The output revealed a Disallow: /juchejaguar/ entry.
2. Attempt to Access the Disallowed Directory: I then attempted to access the /juchejaguar/ path directly using the command 'curl https://juche.msoidentity.com/juchejaguar', which resulted in a 301 Moved Permanently response, indicating that the content had been relocated and that curl needed to be instructed to follow the redirect.
3. Follow the Redirect to Uncover the Flag: To successfully reach the final content, I re-executed the curl command, this time including the -L option to automatically follow redirects: 'curl -L https://juche.msoidentity.com/juchejaguar'. This action successfully retrieved the complete HTML source code of the "Juche Jaguar Secret Lair" page. Upon reviewing the HTML, I located the flag clearly embedded within a div element with the class "Flag" in the <body> section.

<img src="https://github.com/user-attachments/assets/100b00a9-f5a6-4f27-b6be-0e9f0262860b" width="25%" height="25%">
<img src="https://github.com/user-attachments/assets/f983625c-d938-4532-972b-8531495505e3" width="25%" height="25%">
<img src="https://github.com/user-attachments/assets/e51293e0-963c-4f0d-99d9-d302e7775cbd" width="25%" height="25%">
<img src="https://github.com/user-attachments/assets/6404a3f2-3aee-446e-bcb9-a52e24c2b123" width="25%" height="25%">
<img src="https://github.com/user-attachments/assets/aae5135b-d69b-43b8-bebf-e48a0bb23158" width="25%" height="25%">
<img src="https://github.com/user-attachments/assets/8127df43-708d-4236-aa1f-15f1d10a62d2" width="25%" height="25%">

> **Flag:** C1{r0b0ts_arent_4lways_p0lit3}


# Alternative Approach
1. If you don't already have one, create a wordlist with common website suffices. Some examples include `/index.txt`, `/robots.txt`, and `/secret[s].txt`.
2. Download a website fuzzer. Alternatively, I also used [Gobuster](https://github.com/OJ/gobuster), a powerful enumeration and fuzzing tool written in Go.
3. Go to your terminal and run this command: `gobuster dir -u https://juche.msoidentity.com -w common.txt` (or the equivalent command for your chosen website fuzzer).
   - This command runs Gobuster in directory/enumeration mode on the provided URL using the wordlist `common.txt`.
4. Gobuster should return `/robots.txt`.
5. Navigate to hxxps[://]juche[.]msoidentity[.]com/robots[.]txt. You'll see the blocked directory is /juchejaguar/.
6. Navigate to hxxps[://]juche[.]msoidentity[.]com/juchejaguar/, and you'll see the flag!

