# Devasc_Skills_JohanD
Devasc Skills Test
Task name: Task 6 -- Webex Teams API

Task preparation:

	=>Lab 8.6.7: Construct a Pyton script to Manage Webex Teams
	=>Devasc VM
	=> Webex account
	=> Webex Teams Acces Token
	=> VS Code
	=> adapt Lab code
	
Task Implementation:

1. test token with authentication.py

import requests
import json
access_token = 'MDUyZmRhZjQtMTk0Yi00NDllLWE1MWMtMjM4NGJhODBkM2I2NjY2NzhhMWYtZjY2_PF84_d3558e03-2933-4d83-8021-b115db9045d4'
url = 'https://webexapis.com/v1/people/me'
headers = {
 'Authorization': 'Bearer {}'.format(access_token)
}
res = requests.get(url, headers=headers)
print(json.dumps(res.json(), indent=4))

2. list people.py

import requests
import json
access_token = 'MDUyZmRhZjQtMTk0Yi00NDllLWE1MWMtMjM4NGJhODBkM2I2NjY2NzhhMWYtZjY2_PF84_d3558e03-2933-4d83-8021-b115db9045d4'
# Fill in this file with the people listing code from the Webex Teams exercise
person_id = 'Y2lzY29zcGFyazovL3VzL1BFT1BMRS85YzFkYzFjZi1jYTVjLTRhNjEtOWM0MC05MmQ2NWVmNzM5ZjU'
url = 'https://webexapis.com/v1/people/{}'.format(person_id)
headers = {
 'Authorization': 'Bearer {}'.format(access_token),
 'Content-Type': 'application/json'
}
res = requests.get(url, headers=headers)
print(json.dumps(res.json(), indent=4))

3. create-rooms.py

import requests
access_token = 'MDUyZmRhZjQtMTk0Yi00NDllLWE1MWMtMjM4NGJhODBkM2I2NjY2NzhhMWYtZjY2_PF84_d3558e03-2933-4d83-8021-b115db9045d4'
url = 'https://webexapis.com/v1/rooms'
headers = {
 'Authorization': 'Bearer {}'.format(access_token),
 'Content-Type': 'application/json'
}
params={'title': 'devasc_skills_{{Johan_Deld}}'}
res = requests.post(url, headers=headers, json=params)
print(res.json())

4. create-memberships.py

import requests
access_token = 'MDUyZmRhZjQtMTk0Yi00NDllLWE1MWMtMjM4NGJhODBkM2I2NjY2NzhhMWYtZjY2_PF84_d3558e03-2933-4d83-8021-b115db9045d4'
room_id = 'Y2lzY29zcGFyazovL3VzL1JPT00vYTQ5OWNlYzAtMWU3ZS0xMWVlLThlMDAtNmY4YjU1N2RlNDYy'
person_email = 'yvan.rooseleer@biasc.be'
url = 'https://webexapis.com/v1/memberships'
headers = {
 'Authorization': 'Bearer {}'.format(access_token),
 'Content-Type': 'application/json'
}
params = {'roomId': room_id, 'personEmail': person_email}
res = requests.post(url, headers=headers, json=params)
print(res.json())

5. create-markdown-message.py

import requests
access_token = 'MDUyZmRhZjQtMTk0Yi00NDllLWE1MWMtMjM4NGJhODBkM2I2NjY2NzhhMWYtZjY2_PF84_d3558e03-2933-4d83-8021-b115db9045d4'
room_id = 'Y2lzY29zcGFyazovL3VzL1JPT00vYTQ5OWNlYzAtMWU3ZS0xMWVlLThlMDAtNmY4YjU1N2RlNDYy'
message = 'Here are my screenshots of devasc skills-based exam'
url = 'https://webexapis.com/v1/messages'
headers = {
 'Authorization': 'Bearer {}'.format(access_token),
 'Content-Type': 'application/json'
}
params = {'roomId': room_id, 'markdown': message}
res = requests.post(url, headers=headers, json=params)
print(res.json())

Task troubleshooting:

- password error login to webex: reset password for my account 
- wrong personal token 
- wrong room id: message did not appear in webex space

Task verification:

1. authentication.py

devasc@labvm:~/labs/devnet-src/webex-teams$ /bin/python3 /home/devasc/labs/devnet-src/webex-teams/authentication.py
{
    "id": "Y2lzY29zcGFyazovL3VzL1BFT1BMRS85YzFkYzFjZi1jYTVjLTRhNjEtOWM0MC05MmQ2NWVmNzM5ZjU",
    "emails": [
        "johan.deldaele@gmail.com"
    ],
    "phoneNumbers": [],
    "displayName": "johan deldaele",
    "nickName": "johan",
    "firstName": "johan",
    "lastName": "deldaele",
    "userName": "johan.deldaele@gmail.com",
    "orgId": "Y2lzY29zcGFyazovL3VzL09SR0FOSVpBVElPTi9kMzU1OGUwMy0yOTMzLTRkODMtODAyMS1iMTE1ZGI5MDQ1ZDQ",
    "created": "2020-09-30T09:19:55.315Z",
    "lastModified": "2023-04-13T12:55:06.676Z",
    "lastActivity": "2023-07-09T14:40:46.062Z",
    "status": "active",
    "type": "person"
	
2. create-rooms.py

devasc@labvm:~/labs/devnet-src/webex-teams$ /bin/python3 /home/devasc/labs/devnet-src/webex-teams/create-rooms.py
{'id': 'Y2lzY29zcGFyazovL3VzL1JPT00vYTQ5OWNlYzAtMWU3ZS0xMWVlLThlMDAtNmY4YjU1N2RlNDYy', 
'title': 'devasc_skills_{{Johan_Deld}}', 
'type': 'group', 
'isLocked': False, 
'lastActivity': '2023-07-09T17:32:57.132Z', 
'creatorId': 'Y2lzY29zcGFyazovL3VzL1BFT1BMRS85YzFkYzFjZi1jYTVjLTRhNjEtOWM0MC05MmQ2NWVmNzM5ZjU', 
'created': '2023-07-09T17:32:57.132Z', 
'ownerId': 'Y2lzY29zcGFyazovL3VzL09SR0FOSVpBVElPTi9kMzU1OGUwMy0yOTMzLTRkODMtODAyMS1iMTE1ZGI5MDQ1ZDQ', 
'isPublic': False}

3. create-memberships.py

devasc@labvm:~/labs/devnet-src/webex-teams$ /bin/python3 /home/devasc/labs/devnet-src/webex-teams/create-membership.py
{'id': 'Y2lzY29zcGFyazovL3VzL01FTUJFUlNISVAvYWIyY2U1NjQtYTc5Yi00OWM1LTgyM2EtOTJjZWM0OTYyOTBmOjc2ZjgyMWUwLWZlODUtMTFlYS1iMGI4LTM5N2RjODAwNWFhMg', 
'roomId': 'Y2lzY29zcGFyazovL3VzL1JPT00vNzZmODIxZTAtZmU4NS0xMWVhLWIwYjgtMzk3ZGM4MDA1YWEy', 
'roomType': 'group', 
'personId': 'Y2lzY29zcGFyazovL3VzL1BFT1BMRS9hYjJjZTU2NC1hNzliLTQ5YzUtODIzYS05MmNlYzQ5NjI5MGY', 
'personEmail': 'Yvan.rooseleer@biasc.be', 
'personDisplayName': 'Yvan Rooseleer', 
'personOrgId': 'Y2lzY29zcGFyazovL3VzL09SR0FOSVpBVElPTi9lNGQ0MTEyZC0yNTQ4LTRhNDctODEwZS0wNGZlNDVlYTE4MWY', 
'isModerator': False, 
'isMonitor': False, 
'isRoomHidden': False, 
'created': '2023-07-09T17:49:47.098Z'}

4. create-markdown-message.py

devasc@labvm:~/labs/devnet-src/webex-teams$ /bin/python3 /home/devasc/labs/devnet-src/webex-teams/create-markdown-message.py
{'id': 'Y2lzY29zcGFyazovL3VzL01FU1NBR0UvOGU5MTNhMzAtMWU4NS0xMWVlLWEwY2EtZjdkMTM2ZDljNGE0', 
'roomId': 'Y2lzY29zcGFyazovL3VzL1JPT00vYTQ5OWNlYzAtMWU3ZS0xMWVlLThlMDAtNmY4YjU1N2RlNDYy', 
'roomType': 'group', 
'text': 'Here are my screenshots of devasc skills-based exam', 
'personId': 'Y2lzY29zcGFyazovL3VzL1BFT1BMRS85YzFkYzFjZi1jYTVjLTRhNjEtOWM0MC05MmQ2NWVmNzM5ZjU', 
'personEmail': 'johan.deldaele@gmail.com', 
'markdown': 'Here are my screenshots of devasc skills-based exam', 
'html': '<p>Here are my screenshots of devasc skills-based exam</p>', 
'created': '2023-07-09T18:22:26.643Z'}

5. 
   publish the url of your github remote repository in the Webex teams space: done
   upload the screenshots of the skills exam to the webex space: done
