# Udacity Logs Analysis Project
This is an internal reporting tool that produces answers by printing them out in the plain text in the Terminal to the following three questions based on the data in the database:

1) What are the most popular three articles of all time? 
2) Who are the most popular articles authors of all time? 
3) On which days did more than 1% of requests lead to errors? 

This tool is a Python program that uses the psycopg2 module to connect to the database. 

## Getting Started

Download:

Python 3.6.1 from [here] (https://www.python.org/downloads/release/python-361/)

VirtualBox from [here] (https://www.virtualbox.org/wiki/Downloads)

Vagrant from [here] (https://www.vagrantup.com/downloads.html)

VM configuration file by Udacity from [here] (https://d17h27t6h515a5.cloudfront.net/topher/2017/May/59125904_fsnd-virtual-machine/fsnd-virtual-machine.zip) or clone the repository from [here] (https://github.com/udacity/fullstack-nanodegree-vm)

Project Data from [here] (https://d17h27t6h515a5.cloudfront.net/topher/2016/August/57b5f748_newsdata/newsdata.zip)

(For Windows users) Git from [here] (https://git-scm.com/downloads)

(OPTIONAL) Sublime Text from [here] (https://sublimetext.com/2)

### Managing the application

After you downloaded and installed Python3, VirtualBox and Vagrant:

* Open Terminal (Windows users - open Git Bash terminal that comes with the GIT software).

* Change to the "vagrant" directory located in the VM configuration file. 

* To start the virtual machine, inside the vagrant subdirectory, run the command "vagrant up" then "vagrant ssh" to log in to your Linux VM. 

* Unzip Project Data file. Put the file called "newsdata.sql" into the vagrant directory, which is shared with the virtual machine. 

* In the Terminal enter "psql -d news -f newsdata.sql" to connect to the database "news" and run sql commands. 

* Run the command " psql news" to open PostgreSQL command line program 

* (IMPORTANT) This reporting tool uses SQL views to produce an answer to the 3rd question. You will need to create an SQL view with the following command "create view stat as (select ec.date, ec.errors, tc.total from (select time::date as date, count(*) as errors from log where status!='200 OK' group by date) as ec join (select time::date as date, count(*) as total from log group by date) as tc on ec.date=tc.date order by ec.date asc);" 

* After you created the view, exit PostgreSQL command line by running "\q" command.

* Run the command "cd ../../vagrant" to change to the directory containing the project files on the VM. 

* Change directory to "logs analysis"

* Run "python3 newsdatadb.py" to start the tool.  

How to edit the application: 

* open newsdatadb.py in Sublime Text to access the code 

## Built With

* Python 3 
* Python's Psycopg2 module
* Postgresql 

## Author

* Dameli Ushbayeva


