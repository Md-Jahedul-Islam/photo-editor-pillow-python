# Simulation Guide for AHB_UART


## 1. Setup ssh

 Step 1: Open terminal from anywhere. Enter the below command.
  
         $ ssh-keygen -t ecdsa -b 521 -C “your_email@ulkasemi.com”
          
 Step 2 :  Press Enter and type Password. 
           Example: ulka1234
           
 Step 3 : Enter the below command. And copy everything.
 
          $ cat ~/.ssh/id_ecdsa.pub
    
Example : 
“ecdsasha2nistp521AAAAE2VjZHNhLXNoYTItbmlzdHA1MjEAAAAIbmlzdHA1MjEAAACFBAD1lT+lsMYGCjjiLQjUUM23erXD8yy4hc7REtCA0ZZO8+fG0MdK6ZCPwtYTgerxw9e796v57A8OCbcBbX5/fYnZzAGHJka+TRxcuYtsFeaGpA/mefyscldpQf8I1lHtB9266uPii3MM7fIjwOJmk954XI9J70oLUmLNcxpzw2wHps8iXQ==your_email@ulkasemi.com”  copy this.

Step 4 : Goto GitHub Setting > SSH and GPG Keys 

+ Click on New  SSH Key > Paste your ssh-key > Add SSH key

## 2. Clone Git

Step 1 : Copy repo-ssh-link 

Step 2 :  Goto the directory where you want to clone git repository & Enter below command

          $ git clone <repo_ssh_link>          
          Example: $ git clone git@github.com:Md-jahedul-Ulkasemi/git_test.git


## 3. Create New Branch

To create a new local branch : Open terminal in aurora file [internal_proj/ip_dev_ulka/aurora]                                                   
and write the following command
      
            $ git branch <branch_name>
            Example: $ git branch dv_sim_branch
     
To list all local branches: ( current branch)
      
            $ git branch

## 4. checkout to created branch

To switch to a given local branch:
     
       $ git checkout  <branch_name>
       Example: $ git checkout  dv_sim_branch
     
## 5. load Tools on Server

 Server Address: 192.168.10.96
 
 Step 1: Write command : 
 
        $ csh 
 
 Step 2: Source cshrc : 
 
        $ source /silicon/cshrc
        
 Server Address: 192.168.5.90
 
  Step 1: Source cshrc_ius15 : 
 
        $ source /tools/script.cshrc_ius15 
 
 Step 2: Source cshrc : 
 
        $ source /tools/script.cshrc
 
## 6. Run Script: 

Step 1 : Change Directory to /aurora/ips/uart/dv/sim

Step 2 : Resolve bad interpreter issue using following command:

            sed -i -e 's/\r$//' runscript.sh
            
Step 3 : Set Working Directory with the following command:

             export MY_WORKING_DIR=$PWD or setenv MY_WORKING_DIR $PWD
             
Step 4 : Script can be run in 4 different modes. 

 i.  Batch Mode
 
 ii. GUI Mode
 
 iii. Coverage Mode
 
 Iv. Regression Mode
 
### Usage:

| Mode       |          Command                               | Example | 
|------------|------------------------------------------------|---------|
| Batch      | $(basename $0) -b -t_name <testname> -u_vrbs <verbosity> -t_out <timeout> -s_freq <100e6> -s_seed <seed> -i_divl <lower_value> -i_divh <upper_value> -f_divl <lower_value> -f_divh <upper_value> -n_rpt <no_of_repeat> | ./runscript.sh -b -t_name uart_txd_test -u_vrbs UVM_NONE -t_out 980000000 -s_freq 100e6 -s_seed random -i_divl 650 -i_divh 2700 -f_divl 3 -f_divh 16 -n_rpt 5 |
| GUI        | $(basename $0) -g -t_name <testname> -u_vrbs <verbosity> -t_out <timeout> -s_freq <100e6> -s_seed <seed> -i_divl <lower_value> -i_divh <upper_value> -f_divl <lower_value> -f_divh <upper_value> -n_rpt <no_of_repeat> | ./runscript.sh -g -t_name uart_txd_test -u_vrbs UVM_NONE -t_out 92000000 -s_freq 100e6 -s_seed random -i_divl 650 -i_divh 2700 -f_divl 3 -f_divh 16 -n_rpt 8 |
| Coverage   | .$(basename $0) -c -t_name <testname> -u_vrbs <verbosity> -t_out <timeout> -s_freq <100e6> -s_seed <seed> -i_divl <lower_value> -i_divh <upper_value> -f_divl <lower_value> -f_divh <upper_value> -n_rpt <no_of_repeat> | ./runscript.sh -c -t_name uart_rxd_test -u_vrbs UVM_NONE -t_out 82000000000 -s_freq 100e6 -s_seed random -i_divl 650 -i_divh 2700 -f_divl 3 -f_divh 16 -n_rpt 10 |
| Regression | $(basename $0) -r -t_list <testlist> -u_vrbs <verbosity> -t_out <timeout> -s_freq <100e6> -s_seed <seed> -i_divl <lower_value> -i_divh <upper_value> -f_divl <lower_value> -f_divh <upper_value> -n_rpt <no_of_repeat> |  ./runscript.sh -r testlist.txt -u_vrbs UVM_NONE -t_out 82000000000 -s_freq 100e6 -s_seed random -i_divl 650 -i_divh 2700 -f_divl 3 -f_divh 16 -n_rpt 10 |
    
#### Here testlist can be a text file input where several testname are written. 

#### Script can be run with only the follow argument. Rest of the arguments are set default value in script.
 
            $(basename $0) -<b/g/c> -t_name <testname>
 
 
 ## 6. E Manager: 


Step 1: Write the following command to open the  EManger tool

           $emanager &
           
Step 2: Click setup from the pop up emanger window to setup the regression.

Step 3: Press "start" button to start a regression.

Step 4: After that a Start session dialogue box will appear, from where select & open the regression.vsif file.

Step 5: To see the progress press refresh button & wait for progress to be 100%.
 
Step 6: To see coverage report press "vplan" and press "ok" to pop up dialogue box.

Step 7: It will cause to apper another dialogue box called "Automatic Coverage merge", from where select (merge coverage). ALso have to select the "Show this dialogue again" before press Ok.
 
 
 

## Author 

 + Name  : Mahade Hasan
 + Email : mahade@ulkasemi.com
