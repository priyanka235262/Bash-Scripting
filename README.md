# Bash-Scripting

Different types of variables in shell scripts:
1)System Defined Variables:defined and created by OS itslf.These values can be viewd by 'set' command.
2)User Defined Variables: defined by system users and can be viewed by "echo" command


Shortcut in linux: Inode: has metadata of the files 

SuperBlcok in Shell Scripting:
A SuperBlock is basically a program that guves information about regarding a specific file system.GUI:A GUI is used for controlling computer and its applications.It supports different applications.It mostly depends on the OS.

What are the different stages of a linux process it passes through?
a.waiting:In this stage,the linux process waits for a resource.
b.Riunning: In this process,the linyx process is currently being executed
Stopped: In this proces sthe linux process is stopped after succesful execution.
Zombie:the process has stopped but still active in process table.

$1 --> first arguement $2--> 2nd argument
cp $1 $2 - >  copy 
How to get the script name inside a script:$0
echo $?(exit sttaus of previous script) ---> 0 succesful execution

#!/bin/bash
var=$?
if var=0
        then
        echo "the script is running successfully"
else
        echo "the script is not running successfully"
fi

.How to get last line from a file?
tail -1 testfile.txt
cat testfile.txt
How to get last line from a file?
head -1 testfile.txt

How to get 3rd element from each line from a file?
#!/bin/bash
awk '{print $3}'  $1

FUNCTION:How to write a function:
function example {
echo "Hello Leaner"
}

WHILE:
#!/bin/bash
a=0
while [ $a -lt 10 ]
do 
   echo $a
   a = 'expr $a + 1'
done

UNTIL:
#!/bin/bash
a = 10
until [ $a -lt 30 ]
  echo $a
  a = 'exp $a + 1'
done



What makes C sheel more preferable thne Bourne Shell?
1 Lengthy commnads can be used again and again in C shell.
2.All the commnads can be aliased with C shell.
3.The commnad history can be accessed via C shell.

Difference between $@ and $*?
$*

When used without quotes, $* expands to a single string containing all the command-line arguments, separated by the first character of the IFS (Internal Field Separator) variable, which is typically a space.
When used within double quotes ("$")*, $* expands to a single string containing all the arguments, joined together with the first character of IFS.
$@

When used without quotes, $@ expands to a list of individual arguments, just like $*.
When used within double quotes ("$@"), $@ expands to a list of individual arguments, each enclosed in its own set of double quotes. This preserves any spaces or special characters within the arguments.

Test command is used to compare the test strings.

Single Quote and Double Quote: sigle quote:we donot want to evaluate variables to values.
Double Quote: We use it whn all variables need to be evaluated and values should be assigned.

666 i.e. rw-rw-rw is the default permissionsof a file when it is created.
[ -z""] && echo 0 || echo 1

if  [ -z ""] ; then
  echo 0
else
  echo 1
fi

echo ${new: -variable}
echo $* Happy Learning

#!/bin/bash
array={"Hi" "name" "is" "Upasana"}
echo ${array[@]}
echo ${!array[@]}

Crontab: The crontab is a list of commands that you want to run on a regular schedule,and also the name of the command used to manage the list.

tar is the command which needs to be used to take the backup.dfspace:This command is used to check the free disk space in terms of MB.

- Debug  statements can be inserted in the shell script to output/display the info which helps to identity the problem.
- Using "set -x" we can enable debugging in the script.

  Read-only file can be opened as below:
  vi -R <File name>

  #!/bin/bash
  echo "Hello, $LOGNAME
  echo "current date is 'date'"
  echo " useris who i am"
  echo "current directory 'pwd'"

  Q.I want to automate the deployment of an application to multiple servers.How would you achieve this using a shell script?
  -- To automate deployment ,we can write a script that copies our application files to multiple servers and restarts the application server on each service.

  SERVERS("server1.example.com" "server2.example.com")
  APP_PATH= "/home/ubuntu/inex.html"
  DEPLOY_PATH= "/var/www/html"

  for SERVER In ${SERVERS[@]}",do
  echo "Deploying to $SERVER"
  scp -r $APP_PATH user@$SERVER:$DEPLOY_PATH
  ssh user@SERVER "systemctl restart apache2"
  echo "deployment to $SERVER completed"

  Q.Create a script to monitor disk usage and send an alert if usage exceeds 80%?
  #!/bin/bash
  THRESHOLD = 80
  df -H | grep -vE '^Filesystem|tmpfs|cdrom' | awk '{ print $5 " " $1 }' | while read output; do
   usage=$(echo $output | awk '{ print $1}] | sed 's/%/?g')'

  
  Q.Write a script to chcek if a service is running and start if its not.
  #!/bin/bash
  SERVICE = "httpd"
  if ! systemctl is-active --quiet $SERVICE; then
    echo " $SERVICE is not running,starting it...."
    systemctl start $SERVICE
    echo "$SERVICE started"
  else
    echo "$SERVICE is already running"
  
Q.Script to regular backup logs and clean up logs
- #!/bin/bash
- LOG_DIR = "/var/log/myapp"
 BACKUP_DIR="/backup/logs"

find $LOG_DIR -type  f -mtime +7 -exec tar -rvf $BBACKUP_DIR/logs_backup_$(date + %F).tar {} \; -exec rm { }  \;
echo "logs larger than 7 days has been backed up and 

Q.Write a script to automate database backup.
DB_NAME="mydatabase"
DB_USER="debuser"
DB_PASS="dbpass"
BACKUP_DIR="/backup/db"
mysqldump -u $DB_USER -p$DB_PASS $DB_NAME > $BACCKUP_DIR/db_backup_$(date +%F).sql
echo "database backup completed"

Q.File Backup Script:
#!/bin/bash
backup_dir="/path/to/backup"
source_dir="path/to/source"

tar-czf "$backup_dir/backup_$(date+%Y%m%d_%H%M%S).tar.gz""$source_dir"

Q.Write a script ot chcek the sttaus of the services and if any not running to make them run
SERVICES = (nginx, "mysql" "redis")
for $SERVICE in ${SERVICES[@]}";do
  if ! systemctl is -active --quiet $SERVICE ; then
    echo "$SERVICE is not running,restarting it...."
    systemctl restart $SERVICE
    echo "$SERVICE restarted"
  else
    echo "$SERVICE is running"
  fi 
done

In Linux/Unix shell scripting, you can redirect input and output of commands using special symbols:

1. > (Output Redirection)

Purpose: Redirects the standard output (stdout) of a command to a file.
Example:
Bash

ls > file_list.txt 
This command lists the files in the current directory and redirects the output to a file named file_list.txt.
2. < (Input Redirection)

Purpose: Redirects the standard input (stdin) of a command from a file.
Example:
Bash

wc < my_file.txt 
This command reads the contents of my_file.txt and passes them as input to the wc (word count) command.
3. >> (Append Output)

Purpose: Appends the standard output of a command to an existing file.
Example:
Bash

date >> logfile.txt
This command appends the current date and time to the logfile.txt file.
4. 2>&1 (Redirect Standard Error to Standard Output)

Purpose: Redirects the standard error (stderr) of a command to the standard output (stdout).
Example:
Bash

my_command > output.log 2>&1
This command redirects both the standard output and standard error of my_command to the output.log file.
Combining Redirections:

You can combine these redirection operators to achieve different results. For example:

command > output.log 2> error.log: Redirects stdout to output.log and stderr to error.log.
command 2>&1 > output.log: Redirects both stdout and stderr to output.log.
