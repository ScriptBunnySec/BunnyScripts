# BunnyScripts
# For Educatiional Purposes Only 

print('''
Portscanner Powered By:
  _________             __        __      
 /   _____/ ___________|__|______/  |_    
 \_____  \_/ ___\_  __ \  \____ \   __\   
 /        \  \___|  | \/  |  |_> >  |     
/_______  /\___  >__|  |__|   __/|__|     
        \/     \/         |__|            
__________                                
\______   \__ __  ____   ____ ___ __     
 |    |  _/  |  \/    \ /    <   |  |     
 |    |   \  |  /   |  \   |  \___  |     
 |______  /____/|___|  /___|  / ____|     
        \/           \/     \/\/          
''')

import socket
import termcolor


def scan(target, ports):
  print('\n' + ' Starting Scan For: ' + str(target))
  for port in range(1,ports):
    scan_port(target,port)


def scan_port(ipaddress, port):
  try:
    sock = socket.socket()
    sock.connect((ipaddress, port))
    print('[+] Port Opened ' + str(port))
    sock.close()
  except:
    pass


targets = input('[*] Enter Targets To Scan (split them by ,): ')
ports = int(input('[*] Enter How Many Ports You Want to Scan: '))
if ',' in targets:
  print(termcolor.colored(('[*] Scanning Multiple Targets'), 'green'))
  for ip_addr in targets.split(','):
    scan(ip_addr.strip(' '), ports)
else:
  scan(targets,ports)
