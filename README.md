$ export GITHUB_USERNAME=h04d1n1
$ export GIST_TOKEN=<token> // При создании коммита github ругается что в это строчке был токен, поэтому я здесь написал <token>. В самой команде использовал реальный токен 
$ alias edit=nano
$ mkdir -p ${GITHUB_USERNAME}/workspace
$ cd ${GITHUB_USERNAME}/workspace
$ pwd
/home/cola/h04d1n1/workspace
$ cd ..
$ pwd
/home/cola/h04d1n1
$ mkdir -p workspace/tasks/
$ mkdir -p workspace/projects/
$ mkdir -p workspace/reports/
$ cd workspace
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz

--2025-02-21 19:49:30--  https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
Resolving nodejs.org (nodejs.org)... 104.20.23.46, 104.20.22.46, 2606:4700:10::6814:162e, ...
Connecting to nodejs.org (nodejs.org)|104.20.23.46|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9356460 (8.9M) [application/x-xz]
Saving to: ‘node-v6.11.5-linux-x64.tar.xz’

node-v6.11.5-linux-x64.tar.xz                   100%[=====================================================================================================>]   8.92M  12.6MB/s    in 0.7s    

2025-02-21 19:49:31 (12.6 MB/s) - ‘node-v6.11.5-linux-x64.tar.xz’ saved [9356460/9356460]

$ tar -xf node-v6.11.5-linux-x64.tar.xz
$ rm -rf node-v6.11.5-linux-x64.tar.xz
$ mv node-v6.11.5-linux-x64 node
$ ls node/bin
node  npm
$ echo ${PATH}
/home/cola/.local/bin:/home/cola/.local/bin:/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/cola/.dotnet/tools:/snap/bin
$ export PATH=${PATH}:`pwd`/node/bin
$ echo ${PATH}
/home/cola/.local/bin:/home/cola/.local/bin:/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/cola/.dotnet/tools:/snap/bin:/home/cola/h04d1n1/workspace/node/bin
$ mkdir scripts

$ cat > scripts/activate<<EOF
heredoc> export PATH=\${PATH}:`pwd`/node/bin
heredoc> EOF

$ source scripts/activate
$ sudo gem install gist

Fetching gist-6.0.0.gem
Successfully installed gist-6.0.0
Parsing documentation for gist-6.0.0
Installing ri documentation for gist-6.0.0
Done installing documentation for gist after 0 seconds
1 gem installed

$ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
$ export LAB_NUMBER=01
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}

Cloning into 'tasks/lab01'...
remote: Enumerating objects: 74, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 74 (delta 0), reused 1 (delta 0), pack-reused 71 (from 1)
Receiving objects: 100% (74/74), 945.07 KiB | 2.47 MiB/s, done.
Resolving deltas: 100% (20/20), done.

$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ nano REPORT.md
$ gist REPORT.md
Error: Got Net::HTTPUnauthorized from gist: {"message":"Requires authentication","documentation_url":"https://docs.github.com/rest/gists/gists#create-a-gist","status":"401"}
