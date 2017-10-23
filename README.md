#!/urs/bin/env python

import getpass
import sys
import telnetlib

HOST = "172.16.1.101"
USER = raw_input("Enter UserName: ")
PASSWORD = getpass.getpass()

tn = telnetlib.Telnet(HOST)

if password:
    tn.read_until("PASSWORD: ")
    tn.write(password + "\n")

tn.write("show ip int brief\n")
tn.write(" ")
tn.write(" ")
tn.write(" ")
tn.write("exit\n")

print tn.read_all()
