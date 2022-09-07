# Verification Simulation Guide for AHB_UART


## 1. Setup ssh

 Step 1: Open terminal from anywhere. Enter the below command.
          >>> ssh-keygen -t ecdsa -b 521 -C “your_email@ulkasemi.com”
          
 Step 2 :  Press Enter and type Password. 
           Example: ulka1234
           
 Step 3 : Enter the below command. And copy everything.
          >>> cat ~/.ssh/id_ecdsa.pub

Example : 
“ecdsasha2nistp521AAAAE2VjZHNhLXNoYTItbmlzdHA1MjEAAAAIbmlzdHA1MjEAAACFBAD1lT+lsMYGCjjiLQjUUM23erXD8yy4hc7REtCA0ZZO8+fG0MdK6ZCPwtYTgerxw9e796v57A8OCbcBbX5/fYnZzAGHJka+TRxcuYtsFeaGpA/mefyscldpQf8I1lHtB9266uPii3MM7fIjwOJmk954XI9J70oLUmLNcxpzw2wHps8iXQ==your_email@ulkasemi.com”  copy this.

Step 4 : Goto GitHub Setting > SSH and GPG Keys 

Click on New SSH Key > Paste your ssh-key > Add SSH key

## 2. Clone Git

Step 1 : Copy repo-ssh-link 

Step 2 :  Goto the directory where you want to clone git repository & Enter below command

          >>> git clone <repo_ssh_link>          
          Example: >>> git clone git@github.com:Md-jahedul-Ulkasemi/git_test.git


## 3. Create New Branch
      To create a new local branch : Open terminal in aurora file [internal_proj/ip_dev_ulka/aurora]                                                   
      and write the following command
      >>git branch <branch_name>
     
      To list all local branches: ( current branch)
      >>> git branch

## 4. checkout to created branch
     To switch to a given local branch:
     >>> git checkout  <branch_name>
     
## 5. load Tools on Server

 Server Address: 192.168.10.96
 
 Step 1: Write command : csh 
 
 Step 2: source /silicon/cshrc
 
## 6. Run Script: 

Step 1 : Change Directory to /silicon_engineering/project/micro_controller/ip_verification/mpw1/AHB_UART/dv/sim

Step 2 : Script can be run in 4 different modes. 
 i.  Batch Mode
 
 ii. GUI Mode
 
 iii. Coverage Mode
 
 Iv. Regression Mode
 
### Usage:

| Mode       |          Command                               | 
|------------|------------------------------------------------|
| Batch      | ./runscript.sh -b  <testname> <verbosity>      | 
| GUI        | ./runscript.sh -g  <testname> <verbosity>      | 
| Coverage   | ./runscript.sh -c  <testname> <verbosity>      | 
| Regression | ./runscript.sh -c  <testname> <verbosity>      | 
    
Here testlist can be a text file input where several testname are written
& nth jobs mean the number of tests will run parallely. 


