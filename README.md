# network-config-collector
Automate network device config collection

import getpass
import sys
import telnetlib

HOST = "172.16.1.101"
password = getpass.getpass()

tn = telnetlib.Telnet(HOST)

if password:
    tn.read_until("Password: ")
    tn.write(password + "\n")

tn.write("enable\n")
tn.write("cisco\n")
tn.write("show ip int brief\n")
tn.write(" ")
tn.write(" ")
tn.write(" ")
tn.write("exit\n")

print tn.read_all()
