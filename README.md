# Python Network Scanner

This is a simple python script which scan ips in your network. This is used for educational purposes only. Please don't execute a port scanner against any website or IP address without explicit, written permission from the owner of the server or computer that you are targeting.

## Prerequisites

In order to run the python script, your system must have the following programs/packages installed
* Python 3.8: Download it from https://www.python.org/downloads

## Approach
* First need to clone this respiratory
* Run python script script.py using py script.py in the terminal
* The script will ask you to enter the ip address of gateway or server and Starting ip number and ending ip number
* The script will execute and show you the ips whose are live

## Code
```
import socket
from datetime import datetime

# Author @inforkgodara

ip_address = input("IP Address: ")
splitted_ip_digits = ip_address.split('.')
dot = '.'

first_three_ip_digits = splitted_ip_digits[0] + dot + splitted_ip_digits[1] + dot + splitted_ip_digits[2] + dot
starting_number = int(input("Starting IP Number: "))
ending_number = int(input("Ending IP Number: "))
ending_number = ending_number + 1
start_time = datetime.now()

def scan(ip_address):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    socket.setdefaulttimeout(1)
    result = sock.connect_ex((ip_address, 135))
    if result == 0:
        return 1
    else:
        return 0

def execute():
    for ip in range(starting_number, ending_number):
        ip_address = first_three_ip_digits + str(ip)
        if (scan(ip_address)):
            print(ip_address, "is live")

execute()
end_time = datetime.now()
total_time = end_time - start_time

print("Scanning completed in: ", total_time)
```
