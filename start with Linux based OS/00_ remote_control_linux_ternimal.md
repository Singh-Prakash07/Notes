# controling ubuntu terminal from android
  ## using SSH
  1. install openssh on your ubuntu laptop
      + write command in terminal
      ```
      sudo apt update
      sudo apt install openssh-server
      ```
      + Now we have some command to control this openssh-server
      ```
      sudo systemctl status ssh // to check status ( running or not)
      sudo systemctl start ssh  // to start the service
      sudo systemctl stop ssh      // to stop server
      sudo systemctl enable ssh    // to start server automatically on boot
      sudo systemctl disable ssh   // to stop server to automatically start on system boot.
      ```
      + By default SSH listens on port 22, check for SSH server is running on ubuntu.
  2. Find the IP address of your ubuntu laptop
      + write command in terminal
        ```
        hostname -I  // 192.168.200.100 something like this.
        whoami   // to get username of ubuntu os.
        ```
  3. Install an SSH client on your android
        + using playstore download termux(I have used) or juiceSSH or connectBot.
        + In termux write given command ` pkg update && pkg install openssh `.
        + in next step write ` ssh username@laptop-IP-address` eg. if username is `alex` then `ssh alex@192.168.200.100` press enter
        + first time SSH ask if want to accept the server's fingerprint. Type `yes` and press enter.
        + then inter ubuntu password and after entering it. you'll logged into your ubuntu laptop via ssh.
        
