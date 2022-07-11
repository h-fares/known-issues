# known-issues

## Access to localhost was denied on MAC
### The problem:
You try to get http://localhost:7000 or http://localhost:5000 in Chromium and you get this error mesage _Access denied_ with HTTP-Code 403
### Why?
The issue turned out to be coming from the AirPlay receiver listening on Ports 5000 and 7000, which was creating the 403 error.
### Solution
* Be sure that localhost is pointed to 127.0.0.1: by checking the hosts file `sudo nano /etc/hosts`. This line has to be written: `127.0.0.1 localhost`
* Uncheck the "AirPlay Receiver": Go to System Perferences -> Sharing and uncheck the AirPlay Receiver.
