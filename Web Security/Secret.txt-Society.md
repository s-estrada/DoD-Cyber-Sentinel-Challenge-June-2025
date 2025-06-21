**Difficulty: Very Easy**

_Description:_ Our team suspects that a Juche Jaguar developer accidentally left something interesting behind on a [public site](https://juche.msoidentity.com). You’ve been tasked with examining its structure. Can you uncover what the bots were told to ignore? Start with the usual entry points a crawler might explore. One disallowed path leads to a page where someone left behind more than just code.

# Tools Used
curl: A command-line tool used for transferring data with URLs, essential for fetching web content and inspecting page sources.

# Methodology
1. Using curl, I first examined the contents of https://juche.msoidentity.com/robots.txt to identify any disallowed paths. The robots.txt file showed a Disallow: /juchejaguar/ entry, with a suspicious comment hinting at hidden content.
2. Access the Disallowed Path: I attempted to access https://juche.msoidentity.com/juchejaguar directly with curl. This resulted in a 301 Moved Permanently response, indicating a redirect.
3. Follow the Redirect to Find the Flag: I re-ran the curl command, this time instructing it to follow redirects. This action revealed the HTML source code of the "Juche Jaguar Secret Lair" page. Within the <body> section of the HTML, the flag was clearly visible inside a div element with the class "Flag."


![Screenshot 2025-06-21 at 10 50 23 AM](https://github.com/user-attachments/assets/100b00a9-f5a6-4f27-b6be-0e9f0262860b)
![Screenshot 2025-06-21 at 10 51 28 AM](https://github.com/user-attachments/assets/ad41eed3-f1b7-43f3-b933-749202f8084c)
![Screenshot 2025-06-21 at 10 52 56 AM](https://github.com/user-attachments/assets/e51293e0-963c-4f0d-99d9-d302e7775cbd)
![Screenshot 2025-06-21 at 10 53 44 AM](https://github.com/user-attachments/assets/6404a3f2-3aee-446e-bcb9-a52e24c2b123)
![Screenshot 2025-06-21 at 10 54 14 AM](https://github.com/user-attachments/assets/aae5135b-d69b-43b8-bebf-e48a0bb23158)
![Screenshot 2025-06-21 at 10 54 39 AM](https://github.com/user-attachments/assets/8127df43-708d-4236-aa1f-15f1d10a62d2)






# Alternative Approach
1. If you don't already have one, create a wordlist with common website suffices. Some examples include `/index.txt`, `/robots.txt`, and `/secret[s].txt`.
2. Download a website fuzzer. I'm using [Gobuster](https://github.com/OJ/gobuster), a powerful enumeration and fuzzing tool written in Go.
3. Go to your terminal and run this command: `gobuster dir -u https://juche.msoidentity.com -w common.txt` (or the equivalent command for your chosen website fuzzer).
   - This command runs Gobuster in directory/enumeration mode on the provided URL using the wordlist `common.txt`.
4. Gobuster should return `/robots.txt`.
5. Navigate to hxxps[://]juche[.]msoidentity[.]com/robots[.]txt. You'll see the blocked directory is /juchejaguar/.
6. Navigate to hxxps[://]juche[.]msoidentity[.]com/juchejaguar/, and you'll see the flag!

