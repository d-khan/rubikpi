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

# **Configuring Date and Time on RUBIK Pi 3**

This guide explains how to check and configure the date, time, time zone, and automatic NTP synchronization on the RUBIK Pi 3 using the Linux command-line interface (CLI).

## **1. Check the Current Date and Time**

Run:

```bash
date
```

For more detailed information, use:

```bash
timedatectl
```

The output will show information such as:

```text
Local time: Thu 2026-10-01 18:30:00 PDT
Universal time: Fri 2026-10-02 01:30:00 UTC
Time zone: America/Los_Angeles (PDT, -0700)
System clock synchronized: yes
NTP service: active
```

## **2. Set the Time Zone**

To view available time zones:

```bash
timedatectl list-timezones
```

For Pacific Time, set the time zone to:

```bash
sudo timedatectl set-timezone America/Los_Angeles
```

Verify the change:

```bash
timedatectl
```

Using `America/Los_Angeles` automatically handles the change between Pacific Standard Time (PST) and Pacific Daylight Time (PDT).

## **3. Set the Date and Time Manually**

If NTP is enabled, Linux may prevent you from manually changing the system time.

First disable NTP:

```bash
sudo timedatectl set-ntp false
```

Set the date and time using:

```bash
sudo timedatectl set-time "YYYY-MM-DD HH:MM:SS"
```

For example:

```bash
sudo timedatectl set-time "2026-10-01 18:30:00"
```

This sets the date to **October 1, 2026** and the time to **6:30 PM**.

## **4. Verify the Date and Time**

Run:

```bash
date
```

You can also use:

```bash
timedatectl
```

Confirm that the local time and time zone are correct.

## **5. Enable Automatic NTP Synchronization**

After setting the correct date, time, and time zone, enable NTP:

```bash
sudo timedatectl set-ntp true
```

NTP allows the RUBIK Pi to synchronize its clock automatically with network time servers.

## **6. Check NTP Status**

Run:

```bash
timedatectl
```

Look for:

```text
System clock synchronized: yes
NTP service: active
```

You can also check the synchronization status directly:

```bash
timedatectl show
```

Look for:

```text
NTPSynchronized=yes
NTP=yes
```

## **7. If NTP Is Active but Not Synchronized**

You may see:

```text
System clock synchronized: no
NTP service: active
```

This means the NTP service is enabled, but the RUBIK Pi has not successfully synchronized with a time server yet.

First confirm that the Internet connection is working:

```bash
ping -c 4 google.com
```

Then wait briefly and check again:

```bash
timedatectl
```

> Some network administrators do not allow NTP packets to pass through routers


