Ask for help or search for solutions at https://community.letsencrypt.org. See the logfile /var/log/letsencrypt/letsencrypt.log or re-run Certbot with -v for more details.
ubuntu@ip-172-31-41-74:~/opencart$ sudo apt-get install openssl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
openssl is already the newest version (3.0.13-0ubuntu3.1).
openssl set to manually installed.
The following packages were automatically installed and are no longer required:
  python3-compose python3-docker python3-dockerpty python3-docopt python3-dotenv python3-texttable python3-websocket
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
ubuntu@ip-172-31-41-74:~/opencart$ openssl genpkey -algorithm RSA -out partystation.in.key -pkeyopt rsa_keygen_bits:2048
...+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*...+...+..+.............+...+.....+.+.....+.+........+...............+....+......+......+.....+...+...+..........+..+......+....+..+...+.+.....+.+.....+........................+.+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*.........+......+......................+...+........+......+....+..+....+...+...+.........+...+..+.+........+................+.....+.........+.+...+........+....+.....+....+.....+......+.+....................+...+.+.........+.........+.....+...+.......+..+....+..+............+.+..+...+......+.+..+..............................+...+...+....+..+.+.....+.............+..+.............+......+...+...+..+.+...........+.+..+............+....+.........+...........+.+...+...+..............+...+................+..+..........+..+...+...+.+...+..+..........+......+...+.........+..+................+.....+...+............+....+.....+...+......+.+...+......+...........+.+..+......+.........+......+.......+.....+.......+...........+....+...+...+.................+.............+............+.........+.....+...............+.+........+.+...........+.........+.+...+...........+......+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
............+..+....+.................+...+....+..+................+...+..+............+.......+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*.+............+...+......+.+...............+..+..........+......+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*...+........+......+.+..............+...+.......+......+............+.................+..........+......+..+..........+...+.....+.......+..+.+..+.+..+...............+...+.......+..+..........+.....+.............+..+.+............+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
ubuntu@ip-172-31-41-74:~/opencart$ ls
CHANGELOG.md  INSTALL.md  README.md   apigen.neon    composer.json  docker-compose.yml  nginx.conf           phpstan.neon  tools
Dockerfile    LICENSE.md  UPGRADE.md  buildspec.yml  composer.lock  docs                partystation.in.key  storage       upload
ubuntu@ip-172-31-41-74:~/opencart$ openssl req -new -key partystation.in.key -out partystation.in.csr
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:IN
State or Province Name (full name) [Some-State]:Karnataka
Locality Name (eg, city) []:Bangalore
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Partystation
Organizational Unit Name (eg, section) []:online
Common Name (e.g. server FQDN or YOUR name) []:
Email Address []:sing.shekhawat67@gmail.com

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:partystation
An optional company name []:partystation
ubuntu@ip-172-31-41-74:~/opencart$ ls
CHANGELOG.md  INSTALL.md  README.md   apigen.neon    composer.json  docker-compose.yml  nginx.conf           partystation.in.key  storage  upload
Dockerfile    LICENSE.md  UPGRADE.md  buildspec.yml  composer.lock  docs                partystation.in.csr  phpstan.neon         tools
ubuntu@ip-172-31-41-74:~/opencart$ openssl x509 -req -days 365 -in partystation.in.csr -signkey partystation.in.key -out partystation.in.crt
Certificate request self-signature ok
subject=C = IN, ST = Karnataka, L = Bangalore, O = Partystation, OU = online, emailAddress = sing.shekhawat67@gmail.com
ubuntu@ip-172-31-41-74:~/opencart$ ls
CHANGELOG.md  INSTALL.md  README.md   apigen.neon    composer.json  docker-compose.yml  nginx.conf           partystation.in.csr  phpstan.neon  tools
Dockerfile    LICENSE.md  UPGRADE.md  buildspec.yml  composer.lock  docs                partystation.in.crt  partystation.in.key  storage       upload
ubuntu@ip-172-31-41-74:~/opencart$ cat partystation.in.key partystation.in.crt > partystation.in.pem
ubuntu@ip-172-31-41-74:~/opencart$ pwd
/home/ubuntu/opencart
ubuntu@ip-172-31-41-74:~/opencart$ ls
CHANGELOG.md  INSTALL.md  README.md   apigen.neon    composer.json  docker-compose.yml  nginx.conf           partystation.in.csr  partystation.in.pem  storage  upload
Dockerfile    LICENSE.md  UPGRADE.md  buildspec.yml  composer.lock  docs                partystation.in.crt  partystation.in.key  phpstan.neon         tools
ubuntu@ip-172-31-41-74:~/opencart$ vi nginx.conf
ubuntu@ip-172-31-41-74:~/opencart$