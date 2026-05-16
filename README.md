# ThiranexTask2
import nmap
scanner = nmap.PortScanner()
target = '192.168.1.1'
scanner.scan(hosts=target, arguments='-sT')
for host in scanner.all_hosts():
    print(f'Host: {host}')
    print(f'State: {scanner[host].state()}')
    for proto in scanner[host].all_protocols():
        print(f'Protocol: {proto}')
        ports = scanner[host][proto].keys()
        for port in ports:
            print(f'Port: {port}\tState: {scanner[host][proto][port]["state"]}')
