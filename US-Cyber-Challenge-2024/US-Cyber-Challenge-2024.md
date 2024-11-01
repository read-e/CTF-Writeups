# Cyber Quest 2024
Author: Liam Reidy

**Score: 30/34 (88%)**


Below are questions, my answers, and how I got to them. I did not get a perfect score, 4 of my answers are incorrect.  I am unsure if this is due to formatting errors or selecting the wrong answers, since Cyber Quest has not yet released the correct answers.

Score: **30/34** (88%)

[**Fall 2024 Cyber Quest Resources File**](https://uscc.cyberquests.org/assets/cyberquest_fall2024.zip)


## Part 1

**The questions on this page refer to files in the "devon_lee" folder in the following ZIP file:**

**Devon
 Lee is a 57-year old IT technician at Palm Tree Investments, a fin-tech firm that provides investment services in South Florida.  Over a two-year period starting from February 2020, Devon decided to steal customer credit card information from the firm's internal SharePoint server to sell on the dark web.  He also harvested employee personal information – including social security numbers, birth dates, and addresses to create fake IDs, which were in turn used with fabricated pay stubs, bank statements, and tax documents to apply for loans and pay for his extravagant lifestyle.**

**You are being asked to help identify the impact of the theft and possible runaway location of Devon, who's been missing since last week.  Use the customerPII.csv file, evidence.pcap file, TLSkeys.log file, and social media image post to answer the following questions:**



### 1. **How many Palm Tree Investment customers were impacted?  Please format the answer as a four digit number with no commas or decimal points, such as: 1234**

get all the lines with numbers in them (the column names do not have numbers, and if there is a newline at the end of the file that wouldn’t either

```bash
grep -E '[0-9]' customerPII.csv | wc -l
```

answer = `3456`


### 2. **How many credit card issuers were impacted?**

```bash
grep -E -o '^[^,]*' customerPII.csv | sort | uniq -c | sort
```

```
output:
   1 Card Network
 431 American Express
 443 Discover
 478 Mastercard
2104 VISA
```
answer = `4` 

### 3. **Which card issuer was the most impacted?**

```bash
grep -E -o '^[^,]*' customerPII.csv | sort | uniq -c | sort
```

look at the output:
answer = `VISA` 

with 2104 hits if it matters

### 4. **Which email service was used to transfer the complete list of employees?**

Load TLS secrets from the log file in wireshark settings

Wireshark > Preferences > Protocols > TLS > Pre-Master Secret log filename

answer = `Gmail`

### 5. **What is the name of the file that was used to POST /_/upload and exfil employee information?**

answer = `vacation.txt`

searched for a packet that has `/_/upload` in the info section

and then scrolled down to,
```
1306	15.365373	192.168.21.128	142.250.191.133	HTTP2	1429	HEADERS[111]: POST /_/upload?authuser=0&dcp=asu-n&upload_id=ADPycdv1c2BMrF8A_fniFCDcCE8m2YMzxZQKCbLaeMDiKJvOmi0hHOFnxjQA_YCtAPKMCiBApselSL9Nj2bzr4u5KTT6shNs5g&upload_protocol=resumable

Header: x-goog-upload-file-name: vacation.txt
Name Length: 23
Name: x-goog-upload-file-name
Value Length: 12
Value: vacation.txt
[Unescaped: **vacation.txt]**
Representation: Literal Header Field with Incremental Indexing - New Name
```

### 6. **How many employees were listed in the aforementioned file?  Please format your answer as a two digit number, such as: 42**

right after vacation.txt, packet no. 1308 has the data in plain text

answer = `20`
```
Line-based text data: text/plain (21 lines)
Name,SSN,Gender,Birthday,Age,Address(street Address, State Zip Code)\n
Kling Lonny,430-23-4768,male,19910313,31,52193 Kip Inlet Botsfordfurt, Hialeah, FL 33133\n
Thiel Raquel,328-50-0708,female,19710228,51,961 Roberts Centers, Yorkstown, FL 32201\n
Cartwright Akeem,005-14-6192,male,19961218,27,7907 Larkin Cliffs Apt. 754, Little Cuba, FL 32008\n
Hayes Paxton,006-80-1717,male,19700807,53,611 Walter Viaduct, Doral, FL 32003\n
Schneider Zoila,520-40-3737,female,19970119,25,606 Lupe Vista, Sweetwater, FL 33133\n
Towne Alfonso,647-82-8068,male,19790722,43,30675 Mertz Springs, Brownsville, FL 32201\n
Donnelly Aric,672-18-4647,male,19770422,46,3375 Thelma Fall, Orlando, FL 32003\n
Sporer Alaina,520-40-9387,female,19941212,29,728 Lavada Knoll Suite 734, Clamport, FL 32011\n
Dooley Triston,541-73-7583,male,19980722,24,768 VonRueden Stream Suite 186, Proville, FL 32008\n
Auer Ubaldo,425-85-4500,male,19801216,43,931 Schultz Bridge Apt. 967, Hardbrough, FL 32003\n
Huel Pearline,304-90-5792,female,19750301,47,14080 Reilly Walk Suite 693, Queensworth, FL 33133\n
Brown Santos,630-15-3548,male,19701019,52,421 Dale Freeway Apt. 660, Clamport, FL 32003\n
Schaefer Willis,544-15-7965,male,19970423,26,3618 Homenick Crest Apt. 089, Hialeah, FL 32046\n
Adams Ernie,520-42-1683,male,19750223,47,260 Deshawn Prairie, Yorkstown, FL 32054\n
McKenzie Andreane,681-12-0698,female,19801017,42,8196 Werner Hill Apt. 116, Doral, FL 32058\n
Hammes Green,400-90-4128,male,19760816,47,368 Zboncak Street Apt. 079, Little Cuba, FL 32087\n
Smith Jaylon,690-20-2333,male,19880113,34,345 Forrest Tunnel, Doral, FL 32092\n
Bergstrom Sabryna,248-50-0816,female,19820824,41,140 Justus Orchard, Sweetwater, FL 32013\n
Prohaska Shaun,515-04-0355,male,19880310,34,781 Koss Ports Suite 758, Brownsville, FL 32201\n
Hauck Elwin,052-54-5550,male,19810727,41,677 Terry Land Suite 151, Pinebay, FL 32140\n
```


### 7. **What email address was the file sent to? Hint: Try this Wireshark filter: urlencoded-form.key == "red"**

answer = `devon.lee1965@gmail.com`

### 8. **Which country was the "destination" image taken in?**

```bash
exiftool waterfall.jpg
```

12 deg 42' 16.82" N, 104 deg 3' 42.53" E

[https://www.gps-coordinates.net/gps-coordinates-converter](https://www.gps-coordinates.net/gps-coordinates-converter)

answer = `Cambodia`

### 9. **Who is the author of the destination image?**

```bash
exiftool waterfall.jpg
```

answer = `Sharon Lee`

### 10. **What is the most logical reason that Devon would choose to hide in this location?**

**Select one:**

Sell PII on dark web

Currency exchange rate

Beautiful scenery

`Extradition laws` = answer

## Part 2

**The questions on this page refer to files in the "donathan_koebee" folder in the following ZIP file:**

[**Fall 2024 Cyber Quest Resources File**](https://uscc.cyberquests.org/assets/cyberquest_fall2024.zip)

**Donathan Koebbe is a 43-year old engineer who helps build nuclear powered aircraft carriers for the United States Navy.  Donathan was recently suspected of creating a plot to transmit information relating to the design of nuclear ships to a foreign nation.  He sold information known as “Restricted Data” concerning the design of nuclear-powered warships to a person he believed was a representative of a foreign power. In actuality, that person was an undercover FBI agent. Donathan has been charged in a criminal complaint alleging violations of the Atomic Energy Act.**

**You are being asked to decrypt the blueprint file that was provided by Donathan to the agent and help answer questions regarding the process by which Donathan was able to acquire the aircraft blueprints.  Use the provided files including evidence_dk.pcap, email messages between Donathan (Alice Hill) and the FBI agent (Bob Burns), and the encrypted blueprint file to answer the following questions:**

### 11. **What blueprint did Bob Burns request from Alice Hill?**

unencrypted the pdf with `gpg` using the password from the image `liberteegalitefraternite`

Does it want USS Saratoga? CV-60?
answer? = `CV-60`

### 12. **Which tool did Alice use to encrypt the blueprint file?**

**Select one:**

Microsoft Office

WinZIP

`7-Zip` = answer

GnuPG

```bash
strings blueprint > strings.txt

grep 'zip' strings.txt
```

returns 7zip, surely this is not a coincidence. none of the others matched

### 13. **How many pages does the encrypted blueprint file contain?  Please format your answer as a two digit number, such as: 42**

just count the pages

answer = `19`

### 14. **What network utility was downloaded through HTTP and used to exfil the PDF blueprint?**

packet no. 56247

answer = `ncat`

does the text box want netcat?

### 15. **Which server tool was used to host the network utility used to exfil the PDF blueprint?**

**Select one:**

Apache HTTPD

Microsoft IIS

`Python SimpleHTTP` = answer

```
nginx

56315	133.308080	192.168.1.220	192.168.1.146	HTTP	33898	HTTP/1.0 200 OK  (application/x-msdownload)

Server: SimpleHTTP/0.6 Python/3.10.2\r\n
```

### 16. **What tool was used to download the exfil tool?**

**Select one:**

wget

`cURL` = answer

Python requests lib

Mozilla Firefox

Google Chrome

\
packet no. 56247

`User-Agent: curl/7.55.1\r\n`


### 17. **Recover the PDF blueprint that Donathan exfiltrated. When were the blueprints prepared?**

**Select one:**

24 July 1969

10 October 1957 - i think this is the one i chose when i got a higher score? none of them really make sense

`5 January 1947` - this is the only one that is a date *before* the ship was launched, so surely it is this one

25 September 1962

\
metadata from the pdf didn't help ovbiously, and there were dates that this blueprint was signed off but none of them are an option

https://en.wikipedia.org/wiki/USS_Saratoga_(CV-60)f launched in 55, it has to be 5 january 1947 no? by process of elimination

### 18. **A file called "calc_target_offsets" was recovered from the computer hosting the blueprints.  What CVE was likely used by Donathan to gain access to the blueprints?  Please format your answer like this example: CVE-2022-1234**

answer = `CVE-2020-0796`

google the function, the cve is a a 10/10

SMBGhost aka CoronaBlue

https://en.wikipedia.org/wiki/SMBGhost

### 19. **What is the name given to the security vulnerability Donathan used?**

**Select one:**

`CoronaBlue` = answer (https://en.wikipedia.org/wiki/SMBGhost)

EternalBlue

WebExec

ShellShock

Heartbleed

### 20. **What version of Windows was the computer hosting the blueprints likely running?** 

**Select one:**

Windows 10 1803/1809

Windows 10 21H1/21H2

Windows 10 2004/2010

`Windows 10 1903/1909` = answer

because those versions were effected (according to wikipedia at least [https://en.wikipedia.org/wiki/SMBGhost](https://en.wikipedia.org/wiki/SMBGhost))

## Part 3

**The questions on this page refer to the "log.txt" file in the following ZIP file:**

As a new SOC analyst, you are being asked to analyze the log.txt file from an Apache server and answer the following questions:**

line 4176 is of interest with looking for the pw

### 21. **How many POST requests are there?  Please format your answer as a four digit number, such as: 1234**

```bash
grep 'POST' log.txt | wc -l
```

answer = `5499`

### 22. **How many GET requests are there?  Please format your answer as a four digit number, such as: 1234**

```bash
grep 'GET' log.txt | wc -l
```

answer = `1040`

### 23. **How many unique client requested resources are there?  Please format your answer as a three digit number, such as: 123**

```bash
grep -E -o 'GET.*HTTP/1.1' log.txt | sort | uniq -c | sort | wc -l
```

answer = `887`

### 24. **Which client requested resource is the most common (i.e. had the most requests)?**

```bash
grep -E -o 'GET.*HTTP/1.1' log.txt | sort | uniq -c | sort | tail
```

answer = `/DVWA/login.php`

### 25. **How many different HTTP response status codes are represented in this log?  Please format the answer as a one-digit number, such as: 1**

```bash
grep -E -o 'HTTP/1.1" [0-9][0-9][0-9]' log.txt | sort | uniq -c | wc -l
```

answer = `8`

### 26. **How many times does the most commonly appearing HTTP response code in the log file appear?  Please format your answer as a four digit number, such as: 1234**

```bash
grep -E -o 'HTTP/1.1" [0-9][0-9][0-9]' log.txt | sort | uniq -c | sort
```

you gotta look at the output with that query

answer = `3407`

### 27. **What is the entire URI of the most common referer (without quotes)?**

Assuming “-” counts as no referer:

```bash
grep -o '"http[^"]*' log.txt | sort | uniq -c | sort | tail
```

answer = `http://192.168.4.161/DVWA`

## Part 4

**The questions on this page refer to the "ssn.txt" file in the following ZIP file:**

**You are a new security analyst at a bank and are being asked to identify the 7 Social Security Numbers from the `ssn.txt` file that do not conform to the below requirements from the Social Security Administration.**

**Find the 7 moles, one for each requirement listed below:**

- **SSA will only issue SSNs which are 9 digits in the format XXX-XX-XXXX.**
- **SSA will not issue SSNs which are duplicates.**
- **SSA will not issue SSNs beginning with the number “9”.**
- **SSA will not issue SSNs beginning with the number “666” in positions 1 – 3.**
- **SSA will not issue SSNs beginning with the number “000” in positions 1 – 3.**
- **SSA will not issue SSNs with the number “00” in positions 4 – 5.**
- **SSA will not issue SSNs with the number “0000” in positions 6 – 9.**

**You can visit this link for more information: [https://www.ssa.gov/kc/SSAFactSheet--IssuingSSNs.pdf](https://www.ssa.gov/kc/SSAFactSheet--IssuingSSNs.pdf)**

### 28. **Which SSN fails this rule?**
- **SSA will only issue SSNs which are 9 digits in the format XXX-XX-XXXX**

```bash
grep -v '...-..-....' ssn.txt
```

answer = `117-3-8427`

### 29. **Which SSN fails this rule?**
- **SSA will not issue SSNs which are duplicates**

```bash
sort ssn.txt | uniq -d
```

answer = `642-18-3617`

### 30. **Which SSN fails this rule?**
- **SSA will not issue SSNs beginning with the number "9"**

```bash
grep '9..-..-....' ssn.txt
```

answer = `995-99-5192`

31. **Which SSN fails this rule?**
- **SSA will not issue SSNs beginning with the number "666" in positions 1 - 3**

```bash
grep '666-..-...' ssn.txt
```

answer = `666-37-3885`

32. **Which SSN fails this rule?**
- **SSA will not issue SSNs beginning with the number "000" in positions 1 - 3**

```bash
grep '000-..-....' ssn.txt
```

answer = `000-97-7549`

33. **Which SSN fails this rule?**
- **SSA will not issue SSNs with the number "00" in positions 4 - 5**

```bash
grep '...-00-....' ssn.txt
```

answer = `378-00-7651`

34. **Which SSN fails this rule?**
- **SSA will not issue SSNs with the number "0000" in positions 6 - 9**

```bash
grep '...-..-0000' ssn.txt
```

answer = `571-63-0000`
