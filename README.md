# 🧪 Browser Forensics - Cryptominer Lab

This project showcases my forensic investigation of a suspected cryptomining operation hidden within browser activity. Conducted through a Blue Team Labs Online challenge, I used REMnux and a combination of open-source tools to analyze browser data, inspect JavaScript files, and identify malicious behavior tied to a Chrome extension.

![Screenshot_description](https://github.com/mbergin123/browser-forensics-cryptominer/blob/main/images/screenshots/scenario.png?raw=true)

---

## 🧰 Tools Used

| Tool                   | Purpose                                                  |
|------------------------|----------------------------------------------------------|
| FTK Imager             | Load `.ad1` evidence and browse user profiles            |
| BrowserHistoryView     | Analyze browser search activity and history              |
| Notepad (manual review)| Open and inspect extracted JavaScript files              |
| Google Search          | Correlate findings with public intel                     |

---

## 🔍 Investigation Highlights

### 🧭 Browser Profiles Identified

- Located 2 Chrome user profiles inside the USB evidence:
  - `Default`
    
    ![Screenshot_description](https://github.com/mbergin123/browser-forensics-cryptominer/blob/main/images/screenshots/browserprofile-1.png?raw=true)
    
  - `Profile 1`

    ![Screenshot_description](https://github.com/mbergin123/browser-forensics-cryptominer/blob/main/images/screenshots/browserprofile-2.png?raw=true)

    

### 🎨 Theme Discovery

- Detected an installed Chrome theme through extension metadata. I was able to find this fairly quickly by looking at the times when "themes" were searched through Browser History View and compared them to the extenstions file times in FTK:
  - Extension ID: `egnfmleidkolminhjjkaomjefheafbbb`  
  - Extension Name: **"DFP CryptoCurrency Miner"**
  - Description text: "Allows staff members to mine cryptocurrency in the background of their web browser"
  - Correlated to theme: Earth in Space

### 📜 Suspicious Extensions

- Identified a suspicious Chrome extension installed:
  - Extension ID matched known mining scripts
  - Name: `ScreenShader`
  - JavaScript file (`background.js`) contained obfuscated and encoded scripts

### 🧬 JavaScript File Analysis

- Located JavaScript files within:
  - `AppData\Local\Google\Chrome\User Data\Default\Extensions`
- Scripts included:
  - Obfuscation layers
  - Web worker functions linked to CoinHive (deprecated crypto-mining service)

---

## 📸 Key Screenshots

![Extension Directory](https://github.com/mbergin123/browser-forensics-cryptominer/blob/main/images/screenshots/identify-extensionid&exentsionname.png?raw=true)

*Identified suspicious extension folder by ID*

![background.js Snippet](https://github.com/user-attachments/assets/293c3a57-d659-4b7a-b9cc-c38eb11b705a)

*Obfuscated script found in background.js*

![Notepad_javascript](https://github.com/mbergin123/browser-forensics-cryptominer/blob/main/images/screenshots/found-extention-nameforJS.png?raw=true)

*Was able to see Javascript using Notepad*
- Hashes per second: 20
- Public key: b23efb4650150d5bc5b2de6f05267272cada06d985a0

---

## 🎯 Conclusion

This investigation highlights the importance of browser forensics in identifying malware hidden in user profiles and browser extensions. By analyzing profile data and decoding JavaScript, I uncovered a cryptominer that silently leveraged browser resources.

---

## 🔗 Related

- 🔍 [Blue Team Labs Online](https://blueteamlabs.online)
- 🛡️ [REMnux](https://remnux.org)



