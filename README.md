Task 10 -- FILTERING DNAC RESPONSE DATA ***
>Task name: DNAC

>Task Description
Adapt the Python code in the script on the next page in order to obtain a working application that is able to provide the output shown in the output example OUTPUT TASK 10. 

>Task Output Example
Adapt the given Python script in such a wat that it produces the following output. Not all records are shown in the output.

DNAC OUTPUT TASK 10
Current date and time: 
2021-10-29 09:42:23.613764
===
Hostname: c3504.abc.inc
Family: Wireless Controller
MAC: ac:4a:56:6c:7c:00
IP: 10.10.20.51
Software version: 8.5.140.0
Reachability: Reachable
===
Hostname: leaf1.abc.inc
Family: Switches and Hubs
MAC: 84:8a:8d:05:76:00
IP: 10.10.20.81
Software version: 17.3.3
Reachability: Reachable



>Task Execution

1.	Use your virtual DEVASC virtual machine using a connection to the internet.
2.	Copy the sample script on the next page to your Python execution environment. Mind the indentations.
3.	Adapt the script in such a way that the above OUTPUT TASK 10 will be produced. 
4.	Replace all elements showing XXXXXXXX with suitable parameters, variables, keys, names or code.
5.	Take screenshots indicating the success of your actions, add information to the README.md, save and upload your resulting script file to GitHub.

 
DNAC SAMPLE SCRIPT -- WITH 10 MISSING ELEMENTS
import XXXXAXXXX
import datetime
import json
requests.packages.XXXXBXXXX.disable_warnings()

DNAC_scheme = 'https://'
DNAC_authority='sandboxdnac.cisco.com'
DNAC_port=':443'
DNAC_path_token='/dna/system/api/v1/auth/token'
DNAC_path='/dna/intent/api/v1/network-device'
DNAC_user = 'devnetuser'
DNAC_psw = 'Cisco123!'

# DATE AND TIME
print ("Current date and time: ")
print(datetime.XXXXCXXXX)

# TOKEN REQUEST
token_req_url = DNAC_scheme+DNAC_authority+DNAC_path_token
auth = (DNAC_user, DNAC_psw)
req = requests.request('XXXXDXXXX', token_req_url, auth=auth, verify=False)
token = req.json()['Token']

# INVENTORY REQUEST
req_url = DNAC_scheme+DNAC_authority+DNAC_port+DNAC_path
headers = {'X-AUTH-TOKEN': XXXXEXXXX}
resp_devices = requests.request('GET', req_url, headers=XXXXFXXXX, verify=False)
resp_devices_json = resp_devices.json()

# FILTER RESPONSE DATA
for device in resp_devices_json['response']:
    if device['type'] != None:
        print('===')
        print('Hostname: ' + device['hostname'])
        print('Family  : ' + device[''XXXXGXXXX'])
        print('MAC: '+ device['XXXXHXXXX'])
        print('IP: ' + device['XXXXIXXXX'])
        print('Software version: ' + device['softwareVersion'])
        print('Reachability: ' + device['XXXXJXXXX'])

