Lab1_notes

run1 / i-0e35f6ae6f832b112 :
In this run I tried typing out every command from the runbook to practice typing and to start retaining the command structure. I ran into the command "./cobol/bin/account_lookup 999999
echo $?"
And had my first issue. The code was one block but on separate lines which I need to research how to do manually. When they are together on one line the output doesn't account for the 'echo' command. I also got clarity on the ID line. I skimmed through the directions and overlooked that the template for the line was given already. Reading the full list of instructions thoroughly is definitely something I sometimes forget to do.
Unique output line:
```
[ec2-user@ip-172-31-21-126 ~]$ bash SEIR-Foundations/module_1/lesson1_ec2/API/install/install.sh
bash: SEIR-Foundations/module_1/lesson1_ec2/API/install/install.sh: No such file or directory
```


run 2 / instance-id: i-0938a1f57a8ad81d4
I noticed on the instance details screen there is a new item called "Application status". Its right by the status checks so at first I thought I was doing something wrong to have it not checked off.  I also found out how to have multiple lines of input simultaneously in the terminal. One mistake I made was that I typed the echo command incorrectly and followed with the correct command and got an unexpected output. I figured out that I needed to rerun the account lookup command and then the echo command. The echo command relates directly to whatever was ran right before it. In  this run I did the COBOL practice. I did the COBOL core practice and the biggest thing I learned was the command "find". It helped me figure out where to locate different things in the program. It was equally interesting how the cat -c command works when I decoded the accounts.
Unique output:
```
TXN0001             100001000000012550USDPOSTED  INV-1001
TXNMB001            100002000000016000USDPOSTED  INV-1001
TXNMB001            100002000000000000USDREJECTEDINV-1001
TXNMB001            100002000000000000INVREJECTED
TXNMB001            100002000000000000USDREJECTED1001
TXNMB001            187.50000000000000INVREJECTED
TXNMB001            100002000000018750YENPOSTED  INV-1001

```


run 3 / Instance ID   : i-0e5b540d891abda8a
In this run I have mostly memorized the commands to SSH into the EC2. I notice that before I started the assignment, when I used an AMI to launch the template, AWS would give me the root username instead of the ec2-user. I think the next easiest command to memorize would be sudo dnf install -y git. One mistake I have made was not start some of my cd locations with the / key. I'm typing these commands out myself so sometimes I inadvertently forget to add it.
Unique output:
```
INFO:     Started server process [36254]
```


run 4 /  Instance ID: i-0b16e0d3d7bc996e4
the "git clone https://github.com/BalericaAI/SEIR-Foundations.git" command keeps stopping after 2/9 steps being completed. I have referenced the troubleshooting instructions and have had the same result. I fixed things by starting back at the sudo command and restarting the process. 
Unique output:
```
gnucobol is not packaged for AL2023 - building GnuCOBOL 3.2 from source...

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```


run 5 /  instance-id: i-02ac93dc357370d2c
In this run  I followed along with Theo and went from step 0 to 9. We ran the downloads, cloned the git repo, and interacted with the API. I made a template and an AMI from this instance for convenience. One thing I did differently was to connect using the EC2 connect and not use Git Bash
Unique output: 
```
INFO:     Started server process [35277]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```


run 6 / instance ID: i-09772837b75186af8
For this run I SSH connected via Git Bash. I have basically memorized the chmod and ssh command needed. This run is about how quickly and accurately I can type these commands and get through the runbook. A mistake I made quickly was misspelling the git clone command. It began to ask me to provide credentials, but I've learned to not panic and just press ctrl + c. Concatenated the agents file and was able to see the directions that the systems AI follows.
Unique output:
```
Last metadata expiration check: 0:11:18 ago on Sun Nov  1 04:44:14 2026.
Dependencies resolved.
```


run 7 / Instance ID: i-0dc863ad641771cf8
This final run was very monotonous. The process of launching the instance is very simple and stuck in my head. This time I actually scrolled through the user data to see what the script actually entails. I changed the port 80 message that would show on the screen and realized that the script has elements of different coding languages. The print command is reminiscent of python and there is also html elements present as well.
Unique output:
```
INFO:     Started server process [35361]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

---

### Mistakes I made
- Typos that hindered my progress on many occasions
- On one of the runs, the git clone wouldn't work. I think something happened to the sudo command.
- Using certain commands while in the incorrect directory
- I tried to do the cobol practice thinking it would be simple and ended up being late to work. It definitely took a mot more time than I assumed it would.

### Commands I know by heart
- whoami
- pwd
- chmod 400 (keypair.pem)
- ssh -i (keypair.pem) ec2-user@(Public DNS)
- cd /opt/balerica-bank
- echo $?
- ls SEIR-Foundation
- sudo dnf install -y git
- cut -c (range) (filename.txt)

---

## COBOL Practice

Run 2 / instance-id: i-0938a1f57a8ad81d4
Return code 0 = 
```
[ec2-user@ip-172-31-30-206 balerica-bank]$ ./cobol/bin/payment_post TXNMB001 100002 160 USD INV-1001
TXN=TXNMB001
ACCOUNT=100002
AMOUNT=160.00
CURRENCY=USD
STATUS=POSTED
REASON=APPROVED
[ec2-user@ip-172-31-30-206 balerica-bank]$ echo $?
0 
```
`
Return code 4 =
```
[ec2-user@ip-172-31-30-206 balerica-bank]$ ./cobol/bin/account_lookup 999998
ERROR=ACCOUNT NOT FOUND
ACCOUNT=999998
[ec2-user@ip-172-31-30-206 balerica-bank]$ echo $?
4
```

Return code 8 =
```
[ec2-user@ip-172-31-30-206 balerica-bank]$ ./cobol/bin/payment_post TXNMB001 100002 0 USD 1001
TXN=TXNMB001
ACCOUNT=100002
AMOUNT=0.00
CURRENCY=USD
STATUS=REJECTED
REASON=AMOUNT MUST BE GREATER THAN ZERO
[ec2-user@ip-172-31-30-206 balerica-bank]$ echo $?
8
```
`

Return code 12 =
```
[ec2-user@ip-172-31-30-206 ~]$ /opt/balerica-bank/cobol/bin/account_lookup 100001
echo $?
ERROR=CANNOT OPEN data/accounts.dat
FILE-STATUS=35
12
```

Alice's Balance =
```
(venv) [ec2-user@ip-172-31-30-206 balerica-bank]$ cut -c 51-54 /opt/balerica-bank/data/accounts.dat
5000
```

MY TXN ID= 
```
[ec2-user@ip-172-31-30-206 balerica-bank]$ cat data/payments.dat
TXN0001             100001000000012550USDPOSTED  INV-1001
TXNMB001            100002000000016000USDPOSTED  INV-1001
TXNMB001            100002000000000000USDREJECTEDINV-1001
TXNMB001            100002000000000000INVREJECTED
TXNMB001            100002000000000000USDREJECTED1001
TXNMB001            187.50000000000000INVREJECTED
TXNMB001            100002000000018750YENPOSTED  INV-1001
```
