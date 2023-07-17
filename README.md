# Devasc_Skills_JohanD
Devasc Skills Test
TAsk name => REST API & RESTCONF
Task preparation:
  =>Lab 8.3.7: Use RESTCONF to acces an IOS XE Device: part 6 en Part 7: Python to send GET and PUT Request
	=>Devasc VM
	=>CSR1000v VM
	=> VS Code
 
Task Implementation:

-3- put

curl -i -k -X "PUT" "https://192.168.56.107:443/restconf/data/Cisco-IOS-XE-native:native/logging/monitor/severity" \
-H 'Content-Type: application/yang-data+json' \
-H 'Accept: application/yang-data+json' \
-u 'cisco:cisco123!' \
-d $'{
       "severity": "warnings"
}'


#python script
#cfr https://github.com/yroosel/PythonExperiments/blob/9628372e83826c6b2bbb8c3eeed4f42d31b2bf83/restconf/restconf_logging_monitor_put.py
#step 1 create the restconf directory and start the script
import json
import requests
requests.packages.urllib3.disable_warnings()
#step 2 create the variables components of the request
IP_ADDRESS = "192.168.56.101"
RESTCONF_USERNAME = "cisco"
RESTCONF_PASSWORD = "cisco123!"
basicauth = (RESTCONF_USERNAME, RESTCONF_PASSWORD)
warconf = {"severity": "warnings"}
api_url = f"https://{IP_ADDRESS}/restconf/data/Cisco-IOS-XE-native:native/logging/monitor/severity"
headers = {"Accept":"application/yang-data+json",
           "Content-type":"application/yang-data+json"
           }
#step 3 Create a variable to sent the request and store the JSON responce
resp = requests.put(api_url, data=json.dumps(warconf), auth=basicauth, headers=headers, verify=False)
print(resp)

-4- PATCH

curl -i -k -X "PATCH" "https://192.168.56.107:443/restconf/data/Cisco-IOS-XE-native:native" \
-H 'Content-Type: application/yang-data+json' \
-H 'Accept: application/yang-data+json' \
-u 'cisco:cisco123!' \
-d $'{
"native": {
"logging": {
"monitor": {
"severity": "informational"
}
}
}
}'



#python script
#cfr https://github.com/yroosel/PythonExperiments/blob/9628372e83826c6b2bbb8c3eeed4f42d31b2bf83/restconf/restconf_logging_monitor_put.py
#step 1 create the restconf directory and start the script
import json
import requests
requests.packages.urllib3.disable_warnings()
#step 2 create the variables components of the request
IP_ADDRESS = "192.168.56.101"
RESTCONF_USERNAME = "cisco"
RESTCONF_PASSWORD = "cisco123!"
basicauth = (RESTCONF_USERNAME, RESTCONF_PASSWORD)
warconf = {"severity": "informational"}
api_url = f"https://{IP_ADDRESS}/restconf/data/Cisco-IOS-XE-native:native/logging/monitor/severity"
headers = {"Accept":"application/yang-data+json",
           "Content-type":"application/yang-data+json"
           }
#step 3 Create a variable to sent the request and store the JSON response
resp = requests.patch(api_url, data=json.dumps(warconf), auth=basicauth, headers=headers, verify=False)
print(resp)

-5- OTHER get
#python script
#cfr https://github.com/yroosel/PythonExperiments/blob/9628372e83826c6b2bbb8c3eeed4f42d31b2bf83/restconf/restconf_logging_monitor_put.py
#step 1 create the restconf directory and start the script
import json
import requests
requests.packages.urllib3.disable_warnings()
#step 2 create the variables components of the request
IP_ADDRESS = "192.168.56.101"
RESTCONF_USERNAME = "cisco"
RESTCONF_PASSWORD = "cisco123!"
basicauth = (RESTCONF_USERNAME, RESTCONF_PASSWORD)
api_url = f"https://{IP_ADDRESS}/restconf/data/Cisco-IOS-XE-native:native/logging/monitor/severity"
headers = {"Accept":"application/yang-data+json",
           "Content-type":"application/yang-data+json"
           }
#step 3 Create a variable to sent the request and store the JSON response
resp = requests.patch(api_url, data=json.dumps(warconf), auth=basicauth, headers=headers, verify=False)
print (resp.status_code)
print(resp)
#step 4 Format and display the json data received from CSR1000v
response_json = resp.json()
print (json.dumps(response_json, indent=4))

Task troubleshooting => manualy configuration in the crs1000v 
enable -> conf t -> logging monitor

Task verification:
-3- PUT
-4- Patch
-5- Other GET
see document with screenshots

