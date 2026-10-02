> https://www.thundercomm.com/rubik-pi-3/en/docs/notices

# **RUBIK Pi Safety Instructions**

Follow these safety guidelines when setting up, operating, handling, or modifying the RUBIK Pi.

------

## **1. Operating Environment**

### **Temperature & Humidity**

- Operate the RUBIK Pi **indoors only**.
- Recommended operating temperature: **0°C to 50°C**.
- Relative humidity should be **85% or lower (non-condensing)**.
- Do **not** operate the board in misty, wet, or high-humidity environments.

### **Ventilation & Cooling**

- Ensure that the **heat sinks and cooling fans** are functioning properly.
- Do not block ventilation openings or restrict airflow around the board.
- Keep sufficient space around the device for proper cooling.
- Keep the board away from intense heat sources, including:
  - Halogen lamps
  - Welding sparks
  - Lasers
  - Other high-temperature equipment

------

## **2. Power Supply & Shutdown**

### **Before Powering On**

- Complete all required peripheral connections **before powering on** the RUBIK Pi.
- Verify that the power supply meets the required voltage and current specifications.
- Do not use unregulated or improperly designed DIY power supplies.

### **Power Connection**

- Do **not** plug or unplug the DC power connection while the board is energized.
- Avoid frequent power cycling, as repeated abrupt power interruptions may cause hardware or file-system problems.

### **Proper Shutdown Procedure**

Before disconnecting power, shut down Linux properly:

```bash
sudo shutdown -h now
```

Then:

1. Wait for the operating system to shut down completely.
2. Wait for the relevant LEDs to turn off.
3. Disconnect the power supply.

**Important:** Do not simply disconnect power while Linux is running. An improper shutdown can potentially cause data or file-system corruption.

------

## **3. Electrostatic Discharge (ESD) Protection**

Electronic components on the RUBIK Pi can be sensitive to electrostatic discharge.

Before handling the **PCB, GPIO pins, FPC connectors, or other sensitive interfaces**:

- Wear an **anti-static wrist strap**, or
- Touch grounded metal to discharge static electricity before touching the board.

When storing or transporting the RUBIK Pi:

- Place the board inside an **anti-static bag**.
- Avoid placing the board directly on materials that can generate static electricity.

------

## **4. Mechanical Mounting**

- Place the RUBIK Pi on a **stable, flat, and electrically insulated surface**.
- Use appropriate **standoffs** when permanently mounting the board.
- Do not allow the PCB to bend or flex.
- Always handle the board by its **edges**.
- Avoid directly touching electronic components on the PCB.

------

## **5. Peripherals & Interfaces**

### **USB, HDMI, MIPI CSI/DSI**

USB, HDMI, MIPI CSI/DSI, and other peripherals should be connected carefully.

When possible:

1. Shut down the RUBIK Pi.
2. Disconnect power.
3. Connect or disconnect the peripheral.
4. Reconnect power.
5. Start the RUBIK Pi.

### **Storage Devices**

Before removing an SD card, UFS storage device, or other mounted storage:

- Make sure the operating system is no longer using it.
- Unmount the device properly before removal.

For example:

```bash
sudo umount /path/to/mount
```

### **Cables**

- Use **high-quality, well-shielded cables**.
- Avoid unnecessarily long cables.
- Poor-quality or excessively long cables may cause power or signal-integrity problems.

### **GPIO & Expansion Modules**

Before connecting hardware to GPIO pins or expansion interfaces:

- Verify the required **voltage level**.
- Verify the maximum **current rating**.
- Confirm the correct pinout.
- Check polarity before applying power.
- Avoid short circuits between power, ground, and GPIO pins.

**Warning:** Applying an incorrect voltage to a GPIO pin can permanently damage the RUBIK Pi.

------

## **6. Regulatory Compliance & Modifications**

When using the RUBIK Pi with external accessories, wireless devices, power supplies, or enclosures:

- Follow applicable local **electrical safety** requirements.
- Follow applicable **EMC (Electromagnetic Compatibility)** requirements.
- Follow applicable **RF (Radio Frequency)** regulations when wireless equipment is used.

Avoid unauthorized modifications to the PCB.

Do not install uncertified wireless modules or make hardware modifications that could:

- Damage the board
- Create an electrical or thermal hazard
- Cause regulatory compliance issues
- Affect warranty coverage

------

## **Safety Checklist**

Before powering on the RUBIK Pi, verify:

- The board is on a stable, insulated surface.
- The correct power supply is being used.
- All required peripherals are properly connected.
- HDMI and other cables are securely connected.
- Cooling and ventilation are unobstructed.
- GPIO voltage and current requirements have been checked.
- There are no loose conductive objects near the PCB.
- Appropriate ESD precautions have been taken.

Before disconnecting power:

- Save all work.
- Close running applications or processes as appropriate.
- Run `sudo shutdown -h now`.
- Wait for the system to completely shut down.
- Disconnect the power supply.


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



