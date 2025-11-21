# Human Factor In Cybersecurity
Companies invest a lot of money into cybersecurity technology. They will ensure the latest and greatest tools and processes to avoid any vulnerabilities, only to be thwarted by the inevitable weakest link - humans. The research on the Psychology of Human Error, conducted by Stamford University in 2020, revealed that human error was the cause of 88% of cybersecurity data breaches. However, according to the 2023 Thales Global Security Study involving nearly 3,000 companies, human error remains a significant factor, causing 55% of data breaches​ (SWEENEY)​. 

## Case Studies
- Sony Pictures
  - 2014
  - North Korean nation state hackers stole and released 100 terabytes of data from Sony. They sent phishing emails to numerous executives, claiming to be from Apple. When the user clicked the link in the email, they were directed to a fake website and entered their credentials. Due to victims using the same password for both work and their Apple ID, the attackers were able to access Sony's systems.
- Facebook and Google
  - 2013 - 2015
  - An attacker sent fake invoices to Google and Facebook, posing as a legitimate third-party company that they do business with. Over $100 million was stolen from this attack. There were no fancy scripts or firewall penetrations; just a sophisticated social engineering attack.

## Social Engineering
- Human Manipulation
- Tricking individuals into revealing information or granting access
- Relies on the victim's willingness to trust the attacker
<img width="541" height="380" alt="social engineering goals chart" src="https://github.com/user-attachments/assets/64936c29-fda7-45cc-8941-43dac616e530" />

### Methods
- Physical - Tailgating
  - Following behind victim into a restricted area - willing or unwilling
  - "Hey, it's Jim from accounting, we met at the holiday party. Oh yeah, I forgot my keycard at home"
- Pretexting
  - Create a fake scenario to gain trust
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

## The Attack Simulation
The attack targets a person by first identifying the video games they play. By offering a special holiday sale relating to that game, we can entice the victim to click a phishing link that will allow us to steal their credentials when they think they're logging in to the Steam gaming platform. We also explore how malware can be hidden to trick the victim into downloading it. 
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
  - Creates link back to machine that created it
  - Library of fake services to choose from
    - Generates login page that looks like legitimate service
- Victim clicks the phishing link, gets directed to our fake site that looks like Steam, and gives us their credentials
<img width="602" height="311" alt="Blackeye" src="https://github.com/user-attachments/assets/58a8f3c5-2601-4bb3-a83f-a3e884d1ef2d" />

<img width="1379" height="713" alt="blackeye2" src="https://github.com/user-attachments/assets/dc597b3f-220b-4eeb-8de3-72f81c8901ad" />

### Creating the Malware Payload
- Metasploit
  - Create a reverse TCP payload. This is a passive attack, where the malware can sit for any amount of time. Once downloaded and executed, the victim's machine will initiate a shell connection back to the attacker's computer.
<img width="602" height="311" alt="metasploit" src="https://github.com/user-attachments/assets/1008e980-7645-4675-a2e9-52bc4514ee7b" />

  - Disguise payload as a game executable
<img src="https://github.com/user-attachments/assets/b793a1e7-90f7-49df-85fe-ea048fa7f124" />

  - Embed payload and phishing link on website
<img width="1379" height="713" alt="embed_links" src="https://github.com/user-attachments/assets/0c9b4372-4f2c-4474-89e3-1c698a5189de" />


### Delivery method
- Email, Discord, Social Media, QR code on college bulletin board
- Friend/classmate, more trusting

## Impact
In this test scenario, the impact is minimal. The malware is benign and we knew to use fake credentials on the phishing site. This project showed just how easy it was to create and execute believable phishing and malware attacks. With just a little bit of effort, it can be very difficult for the average person to distinguish a legitimate login page from a fake one. People tend to be trusting of others in a casual setting. Talking about your favorite video game seems harmless enough, until it's used against you in a phishing attack. People are the greatest asset of an organization, and also its greatest weakness. The best technical cybersecurity infrastructure is still susceptible to human error, incompetence, or malicious intent.

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


## References
- CNBC. (2019, March 27). Phishing email scam stole $100 million from Facebook and Google. CNBC. https://www.cnbc.com/2019/03/27/phishing-email-scam-stole-100-million-from-facebook-and-google.html
- Perera, D. (2015, April). Researcher: Sony hackers used fake emails. Politico. https://www.politico.com/story/2015/04/sony-hackers-fake-emails-117200.html
- Sweeney, A. (n.d.). The cybersecurity risks caused by human error and how to avoid them. ReadyWorks. https://www.readyworks.com/blog/the-cybersecurity-risks-caused-by-human-error-and-how-to-avoid-them
