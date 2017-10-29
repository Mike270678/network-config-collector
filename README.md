#!/usr/bin/env python
import getpass
import telnetlib

# Ask for username and password
user = raw_input("Enter Username: ")
password = getpass.getpass()

#open myswitch files
f = open('myswitch')

# telnet to device IP in  myswitch file and get show run then save output to new file
for line in f:
     print "Get Running config from  Switch " + (line)
     HOST = line.strip()
     tn = telnetlib.Telnet(HOST)

     tn.read_until("Username: ")
     tn.write(user + "\n")
     if password:
        tn.read_until("Password: ")
        tn.write(password + "\n")

        tn.write("terminal length 0\n")
        tn.write("show run\n")
        tn.write("exit\n")

        readoutput = tn.read_all()
        saveoutput = open("Device" + HOST, "w")
        saveoutput.write(readoutput)
        saveoutput.close
