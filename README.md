# jump.py
Jump.py is a easy to use terminal server style utility to manage SSH connections

## Install:

Download "jump"

git clone https://github.com/arharris2/jump.py.git
cd jump.py | chmod +x jump | sudo mv jump /usr/local/bin/

## Running Jump.py for the first time:

Run jump.py from the terminal with "jump"

The script will look for, and create, a folder and file in your home directory called '.jump/devices.csv'. This is the database from which jump.py will call from. You can onboard devices directly to this file or add devices from within the script. Use the 'edit' keyword at the "Search:" prompt to edit the raw devices.csv file.

## Adding devices to Jump.py:

1. From the "Search:" prompt, type 'connect [x.x.x.x]', the script will then prompt you for a username, you can skip this if you'd like use your systems username to access this device.
2. The script will then attempt to log into the IP address provided, and will prompt you for the password. Your password IS NOT saved. You will need to enter it every time you connect or configure PKI.
3. After you exit the SSH session, the script will prompt you for a hostname, if you do not enter a hostname, the script will use the IP address entered above as the hostname.
4. The device will be saved under the current view which is "Default" by default.

## Bulk Edit
Use the "edit" command to bulk edit the devices file. Uses Nano to edit the file. Exit with Control-X.

## Import from DNA Center
Edit the ~/.jump/state.yaml file and add the information in the following format replacing the bracketed sections with the appropriate information:
```
DNAC:
  [View Name]:
    BASE_URL: https://[URL or IP]
    PASSWORD: [Password]
    USERNAME: [Username]
```
Enter jump.py, change to the appropriate view (changeto [view name]), then run the command "import dnac".

If you're experiencing issues with the import, ensure that the information you provided for the connection to DNA Center is correct and that you can connect.

## Connecting to Saved Devices:

From the "Search:" prompt, type the name of a switch. Jump.py will return any devices that match this search string in your current view. Each device is numbered. You can enter either the number by the device you wish to log into or type the full name of the device.

## Creating New Views:

From the "Search:" prompt, type "new [view]". This will change you to this new view, however, this view will not remain past this session unless a device is added under this view.
## Changing Views:

From the "Search:" prompt, type "changeto" if you'd like to chose from a list of available views. You can change to an available view by typing either the number of the view or typing the name of the view.

If you know the name of the view that you'd like to change to you can enter, "changeto [view name]".

## Connect to Default Gateway

Quickly ssh to the default gateway of the subnet you're currently connected to with the 'gateway' keyword at the "Search:" prompt.

## Open USB-Serial Console

Shortcut to open a USB Serial connection using at /dev/tty.usbserial using 9600 baud.

Tested on Mac OS-X Catalina 10.15.7
