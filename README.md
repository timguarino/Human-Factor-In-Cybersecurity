# Cybersecurity's Greatest Weakness: The Human Factor
Companies invest a lot of money into cybersecurity technology. They will ensure the latest and greatest tools and processes to avoid any vulnerabilities, only to be thwarted by the inevitable weakest link - humans. The research on the Psychology of Human Error, conducted by Stamford University in 2020, revealed that human error was the cause of 88% of cybersecurity data breaches. However, according to the 2023 Thales Global Security Study involving nearly 3,000 companies, human error remains a significant factor, causing 55% of data breaches​ (SWEENEY)​. With such a high percentage of attacks caused by the human factor, we wanted to explore why people fall for these schemes and how they are executed. From this, we can learn how to protect ourselves at home and at work.

## Social Engineering
Social engineering is an easier way to bypass other security measures. It involves manipulating people to gain access or discolse informaiton. Since it relies on the victim's willingness to trust the attacker, typical targets are the elderly or those with little technical knowledge. However, anybody can be a victim of a social engineering attack. Many large organizations have suffered major cyberattacks that began with simple social engineering methods.

<img width="541" height="380" alt="social engineering goals chart" src="https://github.com/user-attachments/assets/64936c29-fda7-45cc-8941-43dac616e530" />

### Methods
- Physical - Tailgating
  - Following behind victim into a restricted area. The victim can be willing or unwilling.
  - "Hey, it's Jim from accounting, we met at the holiday party. Oh yeah, I forgot my keycard at home would you mind letting me in?"
- Pretexting
  - Create a fake scenario to gain trust, usually posing as an authority figure.
  - "I'm caling from IT, we've had some issues with your account, I need your password to fix it"
- Baiting
  - Luring and temptation
  - Leaving a flashdrive for someone to find, they will get curious and plug it in to see what's on it
  - May have something interesting on it to reduce suspicion that it was malicious
- Phishing
  - Sending fake emails, texts, etc.
  - Pose as legitimate trusted entity
  - Attempt to obtain sensitive information (passwords, credit card information)
  - Generic, sent to many people hoping that one will bite
- Spear Phishing
  - A phishing attempt targeted at an individual
  - Tailored to get the highest change of success of success
  - Includes personal details: name, boss' name, job, likes, hobbies, etc.

## Case Studies
- Sony Pictures
  - 2014
  - North Korean nation state hackers stole and released 100 terabytes of data from Sony. They sent phishing emails to numerous executives, claiming to be from Apple. When the user clicked the link in the email, they were directed to a fake website and entered their credentials. Due to victims using the same password for both work and their Apple ID, the attackers were able to access Sony's systems.
- Facebook and Google
  - 2013 - 2015
  - An attacker sent fake invoices to Google and Facebook, posing as a legitimate third-party company that they do business with. Over $100 million was stolen from this attack. There were no fancy scripts or firewall penetrations; just a sophisticated social engineering attack.
- Uber
  - 2022
  - Uber claims an employees credentials were initially purchased on the dark web after a malware attack. The account was protected by MFA, but the employee eventually accepted a login approval request, granting access to the attacker. The attacker was able to access other accounts and elevate their permissions to cause harm.

## The Attack Simulation
To safely and ethically explore social engineering attacks, we created a few simulations in a test environment. For this, we used 3 virtual machines:
  1. Website host
     - Kali linux
     - A fake website containing malicious links
  2. Attack machine
     - Kali linux
     - Created phishing URL and hosted a fake Steam login page
     - Created malware payload to host on website
  3. Victim Computer
     - Windows 10
     - Simulate a victim navigating to the website and clicking the malicious links

The attack targets a person by first identifying the video games they play. By offering a special holiday sale relating to that game, we can entice the victim to click a phishing link that will allow us to steal their credentials when they think they're logging in to the Steam gaming platform.

We also explore how malware can be hidden to trick the victim into downloading it. Since we used a simple payload that does not bypass antivirus, for the attack to be successful we needed to create a specific, but common, scenario. Often when gamers play "cracked" games, they need to disable their antivirus for it to work properly. With this in mind, our simple payload is easily executed. If this was not the case, we would need to use more advanced (and more dangerous) malware that can bypass antivirus software.

### Setup
- Use social engineering to find the most popular video games among a group or individual
  - Discord groups
  - Local game clubs
- Create a fake website to offer special Black Friday deals on those games
  - Simple HTML, CSS, and javascript is more than enough to be convincing
  - A sense of urgency to force the victim to act quickly without thinking too much
<img width="555" height="286" alt="gaming site" src="https://github.com/user-attachments/assets/7bc69c5f-5fe8-485a-89d5-9d5889b94a60" />

<img width="602" height="316" alt="gaming site2" src="https://github.com/user-attachments/assets/2760e83d-36ab-4122-b2bf-98cbe78eb928" />

- The phishing link is diguised as one of the video game offer links
- Another link to download a game contains a malware payload

### Create the Phishing Link
- BlackEye
  - Creates link back to the attack machine that created it
  - contains a library of fake services to choose from when creating the link
    - Generates login page that looks like the legitimate service
- Victim clicks the phishing link, gets directed to our fake site that looks like Steam, and gives us their credentials
<img width="602" height="311" alt="Blackeye" src="https://github.com/user-attachments/assets/58a8f3c5-2601-4bb3-a83f-a3e884d1ef2d" />

<img width="1379" height="713" alt="blackeye2" src="https://github.com/user-attachments/assets/dc597b3f-220b-4eeb-8de3-72f81c8901ad" />

### Creating the Malware Payload
- Metasploit
  - Create a reverse TCP payload. This is a passive attack, where the malware can sit for any amount of time until it gets downloaded. Once downloaded and executed, the victim's machine will initiate a shell connection back to the attacker's computer without the victim knowing.
<img width="602" height="311" alt="metasploit" src="https://github.com/user-attachments/assets/1008e980-7645-4675-a2e9-52bc4514ee7b" />

  - Disguise payload as a game executable
<img src="https://github.com/user-attachments/assets/b793a1e7-90f7-49df-85fe-ea048fa7f124" />

  - Embed payload and phishing link on website
<img width="1379" height="713" alt="embed_links" src="https://github.com/user-attachments/assets/0c9b4372-4f2c-4474-89e3-1c698a5189de" />


### Delivery method
The victim needs to be directed to the fake website. Delivery methods include:
  - Email
  - Discord
  - Social Media
  - QR code on college bulletin board
For our simulation, we sent the link via discord. This can simulate friends sharing a website among each other or convincing strangers that it is legitimate and has a good deal. A person may be more trusting of a classmate than a complete stranger, so discord servers for University students are a prime target in a real-world scenario.


## Impact
In this test scenario, the impact is intentionally minimal. The malware is benign and we knew to use fake credentials on the phishing site. However, it was enough to demonstrate the negative outcomes from such an attack. This project showed just how easy it was to create and execute believable phishing and malware attacks. With just a little bit of effort, it can be very difficult for the average person to distinguish a legitimate login page from a fake one. People tend to be trusting of others in a casual setting. Talking about your favorite video game seems harmless enough, until it's used against you in a phishing attack. 
People are the greatest asset of an organization, and also its greatest weakness. The best technical cybersecurity infrastructure is still susceptible to human error, incompetence, or malicious intent. It is easy to get over-confident and think you're immune to such an attack, but if it can happen to Google, it can definitely happen to you.

## Solutions
- Multi-Factor Authentication
  - Using MFA will mitigate impact of a stolen/phished credential. The attacker will be unable to log in with the password alone, giving the victim additional protections and time to change their password.
- Avoid password re-use
  - Password managers can help to have complex, unique passwords for each account
- Security awareness training
  - Routine training and tests can make users more cyber-conscious and increase awareness. Teaching them signs of phishing and common schemes is one of the biggest mitigating factors.
- Spam filtering
  - Automated email filtering, potential area for AI-powered detection
- Strict physical controls
  - Badge checking
  - Gates that only allow 1 person at a time
  - Privacy screens on monitors and cell phones

### Next Steps
To explore this topic further, we could consider some more advanced techniques. Many of these would require some big ethical considerations in an approved and regulated lab setting.
- Advanced malware
  - It would be fascinating to explore more advanced malware payloads and what can be accomplished before a user notices and remediates their system.
- Malware Hiding Techniques
  - Exploring different ways to hide the malware, such as steganography where the payload is hidden inside an image or text file, making it harder to detect
- Shortened URLs
  - We could use shortened bit.ly URLs to further obfuscate the phishing URL.
- Self-hosted phishing website
  - It would be more of a challenge, but provide more control, to create our own fake Steam login page, using our own fake domain using the domain squatting technique.

## References
- CNBC. (2019, March 27). Phishing email scam stole $100 million from Facebook and Google. CNBC. https://www.cnbc.com/2019/03/27/phishing-email-scam-stole-100-million-from-facebook-and-google.html
- Perera, D. (2015, April). Researcher: Sony hackers used fake emails. Politico. https://www.politico.com/story/2015/04/sony-hackers-fake-emails-117200.html
- Sweeney, A. (n.d.). The cybersecurity risks caused by human error and how to avoid them. ReadyWorks. https://www.readyworks.com/blog/the-cybersecurity-risks-caused-by-human-error-and-how-to-avoid-them
- Uber Technologies, Inc. (2022, September 17). Security update. Uber Newsroom. https://www.uber.com/en-FR/newsroom/security-update/
