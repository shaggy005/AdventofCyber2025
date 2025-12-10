# Linux CLI - Shells Bells
## Which CLI command would you use to list a directory?
```
ls
```
### Flag : ``THM{learning-linux-cli}``
## Which command helped you filter the logs for failed logins?
```
grep
```
### Flag: ``THM{sir-carrotbane-attacks}``
## Which command would you run to switch to the root user?
```
sudo su
```
Finally, what flag did Sir Carrotbane leave in the root bash history?
```
THM{until-we-meet-again}
```
## Side Quest
For those who consider themselves intermediate and want another challenge, check McSkidy's hidden note in /home/mcskidy/Documents/ to get access to the key for Side Quest 1! Accessible through our Side Quest Hub!
### Solution:
- I explored the entire machine for an hour checked all of mcskiddy's and eddi_knapp
- cant copy all my terminal history cause its a novel and a half so here's what i found
```
mcskidy@tbfc-web01:~/Documents$ cat read-me-please.txt 
From: mcskidy
To: whoever finds this

I had a short second when no one was watching. I used it.

I've managed to plant a few clues around the account.
If you can get into the user below and look carefully,
those three little "easter eggs" will combine into a passcode
that unlocks a further message that I encrypted in the
/home/eddi_knapp/Documents/ directory.
I didn't want the wrong eyes to see it.

Access the user account:
username: eddi_knapp
password: S0mething1Sc0ming

There are three hidden easter eggs.
They combine to form the passcode to open my encrypted vault.

Clues (one for each egg):

1)
I ride with your session, not with your chest of files.
Open the little bag your shell carries when you arrive.

2)
The tree shows today; the rings remember yesterday.
Read the ledger’s older pages.

3)
When pixels sleep, their tails sometimes whisper plain words.
Listen to the tail.

Find the fragments, join them in order, and use the resulting passcode
to decrypt the message I left. Be careful — I had to be quick,
and I left only enough to get help.

~ McSkidy
```
```
mcskidy@tbfc-web01:/home$ sudo su
root@tbfc-web01:/home$ cd eddi_knapp/
root@tbfc-web01:/home/eddi_knapp$ ls -a
.              .lesshst              Desktop
..             .local                Documents
.bash_history  .pam_environment      Downloads
.bash_logout   .pam_environment.bak  Music
.bashrc        .profile              Pictures
.bashrc.bak    .profile.bak          Public
.cache         .secret               Templates
.config        .secret_git           Videos
.gnupg         .secret_git.bak       fix_passfrag_backups_20251111162432
.image_meta    .viminfo              wget-log
root@tbfc-web01:/home/eddi_knapp$ cat .bash
cat: .bash: No such file or directory
root@tbfc-web01:/home/eddi_knapp$ cat .bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
DELETED A LOT OF UNIMPORTANT STUFF IN BETWEEEN
export PASSFRAG1="3ast3r"
root@tbfc-web01:/home/eddi_knapp$ 
```
inside documents there was a gpg encrypted file, so i tried opening it, but it didnt open so im guessing the passphrase must open it.
```
root@tbfc-web01:/home/eddi_knapp/Documents$ ls -a
.  ..  mcskidy_note.txt.gpg  notes_on_photos.txt
root@tbfc-web01:/home/eddi_knapp/Documents$ 
```
- so there's a passphrase to something
- now in the pictures directory i found a second passphrase (or 3rd part of it apparently)
```
eddi_knapp@tbfc-web01:~/Pictures$ cat  .easter_egg
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@@%%%%@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@#+==+*@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@%+=+*++@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@*++**+#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@%%#*====+#%@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@#*===-===#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@%*++:-+====*%@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@%*===++++===-+*#######%%@@@@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@%*+===+++==::-=========+*#%@@@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@%%#**+======-:-==--==-==+*%@@@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@%*+======---=+===------=#%@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@%**+=-=====-==+==-====--=*%@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@%***+++==--=====+=----=-=#@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@%#**++=--=====++====----*@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@%*+=-:=++**++**+=-::--*@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@@#+=:.+#***=*#=--::-=-=%@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@%%*+-:+%#+++=++=:::==--*%@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@%*+=--*@#++===::::::::=#%@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@%%%##*#%%%####***#*#####%%@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@@@@@@@%%###%%%%%%%%%%##%%##%%@@@@@@@@@@@@

~~ HAPPY EASTER ~~~
PASSFRAG3: c0M1nG
```
- there was ahidden folder ``.secret`` and ``.secret_git``
- so i checked them as they were interesting.
```
eddi_knapp@tbfc-web01:~/.secret_git$ git log
commit e924698378132991ee08f050251242a092c548fd (HEAD -> master)
Author: mcskiddy <mcskiddy@robco.local>
Date:   Thu Oct 9 17:20:11 2025 +0000

    remove sensitive note

commit d12875c8b62e089320880b9b7e41d6765818af3d
Author: McSkidy <mcskiddy@tbfc.local>
Date:   Thu Oct 9 17:19:53 2025 +0000

    add private note
eddi_knapp@tbfc-web01:~/.secret_git$ git checkout d12875c8b62e089320880b9b7e41d6765818af3d
Note: switching to 'd12875c8b62e089320880b9b7e41d6765818af3d'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at d12875c add private note
eddi_knapp@tbfc-web01:~/.secret_git$ ls
secret_note.txt
eddi_knapp@tbfc-web01:~/.secret_git$ cat secret_note.txt 
========================================
Private note from McSkidy
========================================
We hid things to buy time.
PASSFRAG2: -1s-
```
so here is the second part of the passphrase and together they say: ``3ast3r-1s-c0M1nG``
now i tried the passphrase on the gpg file, heres what it says
```
Congrats — you found all fragments and reached this file.

Below is the list that should be live on the site. If you replace the contents of
/home/socmas/2025/wishlist.txt with this exact list (one item per line, no numbering),
the site will recognise it and the takeover glitching will stop. Do it — it will save the site.

Hardware security keys (YubiKey or similar)
Commercial password manager subscriptions (team seats)
Endpoint detection & response (EDR) licenses
Secure remote access appliances (jump boxes)
Cloud workload scanning credits (container/image scanning)
Threat intelligence feed subscription

Secure code review / SAST tool access
Dedicated secure test lab VM pool
Incident response runbook templates and playbooks
Electronic safe drive with encrypted backups

A final note — I don't know exactly where they have me, but there are *lots* of eggs
and I can smell chocolate in the air. Something big is coming.  — McSkidy

---

When the wishlist is corrected, the site will show a block of ciphertext. This ciphertext can be decrypted with the following unlock key:

UNLOCK_KEY: 91J6X7R4FQ9TQPM9JX2Q9X2Z

To decode the ciphertext, use OpenSSL. For instance, if you copied the ciphertext into a file /tmp/website_output.txt you could decode using the following command:

cat > /tmp/website_output.txt
openssl enc -d -aes-256-cbc -pbkdf2 -iter 200000 -salt -base64 -in /tmp/website_output.txt -out /tmp/decoded_message.txt -pass pass:'91J6X7R4FQ9TQPM9JX2Q9X2Z'
cat /tmp/decoded_message.txt

Sorry to be so convoluted, I couldn't risk making this easy while King Malhare watches. — McSkidy
```
