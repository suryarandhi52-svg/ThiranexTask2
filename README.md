# ThiranexTask2
import nmap

# Create an instance of PortScanner
scanner = nmap.PortScanner()

# Specify the target IP or hostname
target = '192.168.1.1'  # Replace with your target

# Run a basic TCP scan on common ports
scanner.scan(hosts=target, arguments='-sT')

# Print out the results
for host in scanner.all_hosts():
    print(f'Host: {host}')
    print(f'State: {scanner[host].state()}')
    for proto in scanner[host].all_protocols():
        print(f'Protocol: {proto}')
        ports = scanner[host][proto].keys()
        for port in ports:
            print(f'Port: {port}\tState: {scanner[host][proto][port]["state"]}')
