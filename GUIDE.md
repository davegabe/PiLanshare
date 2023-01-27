# Pilanshare Remote

I have made this version of Pilanshare to be able to use my Raspberry as a WiFi bridge and also as a Wake On Lan server.

In order to use it for this purpose, you need also to make it accessible from the internet. I have used [pivpn](https://github.com/pivpn/pivpn), so that it can be used also for other purposes.

## Installation

This is a guide on how to install Pilanshare Remote on a Raspberry Pi from scratch.
Install the latest version of Raspbian on your Raspberry Pi and connect it to your network.
Update the system and install all the updates.

```bash
sudo apt-get update
sudo apt-get upgrade
```

Install pivpn as described in the pivpn installation guide.
Make sure to choose the *wlan0* interface when asked for it and select Wireguard as VPN protocol.

```bash
curl -L https://install.pivpn.io | bash
```
After the installation, you should create a new user (using ```pivpn add```) and connect to the VPN with it.

Install the latest version of Pilanshare Remote.

```bash
wget https://raw.githubusercontent.com/davegabe/PiLanshare/v0.3.3-beta/install.py
sudo apt install python3-distutils
sudo python3 ./install.py -v
rm ./install.py
```

Now you can just connect the computer you want to use to the ethernet port of the Raspberry Pi and turn it on.
Check in the Pilanshare Remote web interface that the computer is visible in the devices list (it's the only one that has *eth0* as interface).
Now you can use the power button to turn on the computer.

## Troubleshooting

If you have problems with the Wake On Lan feature, you should check if your NIC supports it and if it's enabled in the BIOS.

If you can't connect to the VPN, check if the port forwarding is correctly set up (default port is 51820).