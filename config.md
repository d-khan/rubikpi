# **Changing the Console Font Size on RUBIK Pi 3**

If the RUBIK Pi 3 is connected directly to a monitor and you are using the Linux command-line interface (CLI), you can change the console font and font size using `console-setup`.

## **1. Open Console Setup**

Run the following command:

```bash
sudo dpkg-reconfigure console-setup
```

## **2. Select the Encoding**

When prompted for **Encoding to use on the console**, select:

```text
UTF-8
```

Press **Enter**.

## **3. Select the Character Set**

When prompted for the **Character set to support**, select:

```text
Guess optimal character set
```

Press **Enter**.

## **4. Select the Console Font**

Select:

```text
Terminus
```

Press **Enter**.

## **5. Select the Font Size**

For a larger and more readable font, select:

```text
16x32
```

If `16x32` is too large, try:

```text
12x24
```

## **6. Apply the New Font**

After completing the configuration, run:

```bash
sudo setupcon
```

The new console font should be applied immediately.

## **Changing the Font Again**

If you want to change the font or font size later, run:

```bash
sudo dpkg-reconfigure console-setup
```

Then repeat the configuration steps above.

# **How to check the network**

## Check network devices
```
nmcli device status
```

## Turn Wi-Fi on
```
nmcli radio wifi on
```

## Find Wi-Fi networks
```
nmcli device wifi list
```

## Connect securely and be prompted for the password
```
nmcli --ask device wifi connect "YOUR_WIFI_NAME"
```

## Check connection
```
nmcli device status
```

## Check IP address
```
hostname -I
```

## Test Internet
```
ping -c 4 google.com   # sometimes router blocks ICMP protocol
```

## Show saved connections
```
nmcli connection show
nmcli device status
```
```

