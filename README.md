# s5ssh

The technique we used here is called `socks5 over ssh dynamic port forwarding`. 

You may find this [article](https://ma.ttias.be/socks-proxy-linux-ssh-bypass-content-filters/) helpful.

All your traffic is encrypted. 

## Config on Windows

- Prerequisite (Action on our side):
  - Register your IP block into our whitelist. 
  - Send you ssh private key

- Create tunnel:
  - Make sure you have a ssh **private key** called `apq.pem` under your `~/.ssh` (corresponds to `C:\Users\__YOU_USER_NAME__\.ssh` in windows)
    - make sure you replace `__YOU_USER_NAME__`.
    - private key will be generated and shared in a more discrete way.
  - In `PowerShell`, input `ssh -D 1337 -C -N -i /home/runner/.ssh/apq.pem __DNS_NAME__`, `Enter`
    - Please find the `__DNS_NAME__` in [this workflow](https://github.com/HiddenLand/s5ssh/actions/workflows/starts.yml)
    - FYI, the server is up and down from time to time for cost-saving purposes. If you have admin access you can trigger server start with same workflow above
  
- Configure Firefox
  - Go to `Settings`, search for `Proxy`. You will get only one item revealed - `Network Settings`
  - In `Network Settings`, 
    - choose `Manual proxy configuration`
      - `SOCKS Host`: `localhost`
      - `Port`: `1337`
    - Select `Proxy DNS when using SOCKS v5`
  - try to access `www.google.com`. 


