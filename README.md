# Devasc_Skills_JohanD
Devasc Skills Task10
Task Name: DNAC
Task Preparation: 
  =>Devasc VM with python
  =>Visual Studio
  =>DNA sample script: resolve 10 missing elements: Github page YRoosel DNA Center 1 Northbound API Hello Network Simple.py
  =>new DNAC branch on Github
Task implementation:
  =>Adapt the DNAC sample script in a text editor and save it as DNAC_task10.py
  =>run the script in a terminal -> succes
  =>upload script to github
Task Troubleshooting
  =>File "DNAC_task10.py", line 4, in <module>
    requests.packages.urllib3.disable_warnings()
    NameError: name 'requests' is not defined
   => import request was wrong 
   => changed that to import requests
Task verification:
   => devasc@labvm:~/Devasc_Skills$ python3 DNAC_task10.py 
      Current date and time: 
      2023-07-02 23:32:39.761150
      ===
      Hostname: sw1
      Family  : Cisco Catalyst 9000 UADP 8 Port Virtual Switch
      MAC: 52:54:00:01:c2:c0
      IP: 10.10.20.175
      Software version: 17.9.20220318:182713
      Reachability: Reachable
      ===
      Hostname: sw2
      Family  : Cisco Catalyst 9000 UADP 8 Port Virtual Switch
      MAC: 52:54:00:0e:1c:6a
      IP: 10.10.20.176
      Software version: 17.9.20220318:182713
      Reachability: Reachable
      ===
      Hostname: sw3
      Family  : Cisco Catalyst 9000 UADP 8 Port Virtual Switch
      MAC: 52:54:00:0a:1b:4c
      IP: 10.10.20.177
      Software version: 17.9.20220318:182713
      Reachability: Reachable
      ===
      Hostname: sw4
      Family  : Cisco Catalyst 9000 UADP 8 Port Virtual Switch
      MAC: 52:54:00:0f:25:4c
      IP: 10.10.20.178
      Software version: 17.9.20220318:182713
      Reachability: Reachable
      devasc@labvm:~/Devasc_Skills$ 
