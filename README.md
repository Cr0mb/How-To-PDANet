# Turn Your PC into a Free Unlimited Hotspot Using Only Phone Service

## Acknowledgment
The information presented here is based on my personal knowledge and experience over the years. I’m sharing this open-source material to help others.

## iPhone Compatibility
Please note that PDANet does not support iPhone devices for tethering. This is due to the closed nature of iOS and its restrictions on USB tethering and third-party applications. As a result, PDANet is only compatible with Android devices.

## PDANet Tutorial
PDANet (Portable Data Network) is a powerful tool for tethering your device's internet connection. This tutorial will guide you through the installation and configuration process.

### Table of Contents
+ Chapter 1: Getting Started
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Usage](#usage)
  - [Troubleshooting](#troubleshooting)
  - [Downloading OEM and ADB Drivers](#downloading-oem-and-adb-drivers)
+ Chapter 2: Sharing Your Connection
  - [Turning Your PC into a Hotspot After Tethering](#turning-your-pc-into-a-hotspot-after-tethering)
  - [Sharing USB Tether from PC to Another Device via Ethernet](#sharing-usb-tether-from-pc-to-another-device-via-ethernet)
  - [Connection Issues with Video Games and Sites](#connection-issues-with-video-games-and-sites)
+ Chapter 3: Windows Performance Optimization
  - [Understanding PdaNet on Windows](#understanding-pdanet-on-windows)
  - [Critical: Disable USB Selective Suspend](#critical-disable-usb-selective-suspend)
  - [Network Interface Priority (Metric)](#network-interface-priority-metric)
  - [Power Plan Configuration](#power-plan-configuration)
  - [TCP/IP Optimization Settings](#tcpip-optimization-settings)
  - [DNS Configuration](#dns-configuration)
  - [Verifying Your Optimized Configuration](#verifying-your-optimized-configuration)
  - [Quick Optimization Checklist](#quick-optimization-checklist)



### Requirements
- Android device with PDANet installed
- USB cable (for USB tethering)
- A computer with internet access
- A compatible operating system (Windows, macOS, Linux)
- Correct OEM and ADB drivers for your specific phone model

### Installation
1. **Download PDANet:**
   - Visit the [PDANet official website](https://pdanet.co/) and download the latest version for your device.

2. **Install on Android:**
   - Open the downloaded APK file on your Android device and follow the prompts to install.

3. **Install on PC:**
   - For Windows, download and install the PDANet desktop client.
   - For macOS or Linux, follow the instructions provided on the PDANet website.

### Configuration
1. **Enable USB Debugging:**
   - On your Android device, go to **Settings > About phone** and tap **Build number** 7 times to enable Developer Options.
   - Go back to **Settings > Developer options** and enable **USB debugging**.

2. **Connect Your Device:**
   - Use a USB cable to connect your Android device to your computer. Ensure the cable supports file transfer capabilities.

3. **Open PDANet:**
   - Launch the PDANet application on both your Android device and your computer.

4. **Select Tethering Mode:**
   - Choose your preferred tethering method: USB, Wi-Fi, or Bluetooth.

### Usage
#### USB Tethering
- After connecting, select **USB Tether** in the PDANet app on your phone.
- On your computer, you should see a new network connection established.

#### Wi-Fi Tethering
- In the PDANet app, select **Wi-Fi Hotspot**.
- Configure the hotspot settings (SSID, password) and enable it.
- Connect your other devices to the newly created Wi-Fi network.

#### Bluetooth Tethering
- Pair your Android device with your computer via Bluetooth.
- In the PDANet app, select **Bluetooth DUN**.
- Follow the prompts to connect.

### Troubleshooting
- **Connection issues:**
  - Ensure USB debugging is enabled.
  - Verify that you’re using a USB cable that supports file transfer (not a charge-only cable).
  - Make sure the correct OEM and ADB drivers are installed for your phone.
  - Try a different USB port (prefer USB 3.0 ports - usually blue).
  - Check Device Manager for any yellow warning icons on USB or network devices.

- **Slow internet speed:**
  - Try disconnecting and reconnecting your device.
  - Check for background applications consuming bandwidth.
  - **Disable USB Selective Suspend** - this is the #1 cause of USB tethering slowdowns (see [Chapter 3](#critical-disable-usb-selective-suspend)).
  - Ensure your phone has good cellular signal.
  - Check your carrier isn’t throttling your data.

- **Intermittent disconnections:**
  - Disable USB Selective Suspend in Power Options.
  - Use a shorter, high-quality USB cable.
  - Ensure your phone isn’t overheating.
  - Check if your phone’s battery saver mode is interfering.

- **High latency/ping spikes:**
  - Disable USB Selective Suspend (causes latency spikes when USB resumes from suspend).
  - Set PdaNet interface metric to a low value (5) for routing priority.
  - Use faster DNS servers (1.1.1.1 instead of carrier DNS).
  - See [TCP/IP Optimization Settings](#tcpip-optimization-settings) for advanced tuning.

- **Ping tests show "Request timed out":**
  - This is often normal! Many mobile carriers block ICMP (ping) traffic.
  - Your connection may still work fine - test with actual web browsing or TCP connections.
  - To test TCP connectivity instead of ICMP:
    ```powershell
    Test-NetConnection -ComputerName google.com -Port 443
    ```

### Downloading OEM and ADB Drivers
You can download OEM and ADB drivers from several sources:

1. **Manufacturer's Website:**
   - Most device manufacturers provide their own ADB and OEM drivers. You can find most on the Android developer page.

2. **Universal ADB Drivers:**
   - A good option is the [Universal ADB Driver](https://adbdriver.com/).

3. **SDK Platform Tools:**
   - If you have Android Studio, you can get ADB drivers as part of the SDK Platform Tools.

#### Installation Steps
1. Download the appropriate driver.
2. Extract the files (if they are in a ZIP format).
3. **Install the driver:**
   - For Windows, connect your device via USB, open Device Manager, find your device under "Other devices" or "Android Devices," right-click, and choose "Update driver." Select "Browse my computer for driver software" and navigate to the folder where you extracted the driver.

---

## Turning Your PC into a Hotspot After Tethering

1. **Connect Your Android Device:**
   Ensure your Android device is connected to your PC via USB and that PDANet is running, providing internet access.

2. **Open Network & Internet Settings:**
   - **Windows:** Right-click the network icon in the system tray and select "Open Network & Internet settings."
   - **macOS:** Go to System Preferences > Sharing.

3. **Set Up the Hotspot:**
   - **Windows:**
     1. Click on "Mobile hotspot" on the left pane.
     2. Toggle the switch to "On."
     3. Under "Share my Internet connection from," select the network that corresponds to the PDANet connection (usually listed as Ethernet).
     4. Configure your network name (SSID) and password if desired.

   - **macOS:**
     1. Check the box next to "Internet Sharing" in the list on the left.
     2. From the "Share your connection from" dropdown, select "Ethernet" (which is your tethered connection).
     3. Under "To computers using," check "Wi-Fi."
     4. Click "Wi-Fi Options" to configure your network name, security, and password.
     5. Finally, check the box next to "Internet Sharing" to enable the hotspot.

4. **Connect Devices:**
   Use the SSID and password you set up to connect other devices (like smartphones, tablets, etc.) to your new hotspot.

## Sharing USB Tether from PC to Another Device via Ethernet

1. **Ensure Tethering is Active:**
   Make sure PDANet is running and your Android device is connected via USB, providing internet access to your PC.

2. **Connect Your PC to the Game Console:**
   - Use an Ethernet cable to connect your PC to your Xbox or PS4.

3. **Configure Ethernet Sharing on Windows:**
   1. Open "Network and Sharing Center."
   2. Click on "Change adapter settings" on the left.
   3. Right-click on the PDANet connection (usually named "Ethernet") and select "Properties."
   4. Go to the "Sharing" tab.
   5. Check the box for "Allow other network users to connect through this computer's Internet connection."
   6. In the dropdown menu, select the Ethernet connection that connects to your Xbox or PS4.
   7. Click "OK" to save the settings.

4. **Configure Network Settings on Console:**
   - **Xbox:**
     1. Go to "Settings" > "Network" > "Network settings."
     2. Select "Wired Network" and test the connection.
   - **PS4:**
     1. Go to "Settings" > "Network" > "Set Up Internet Connection."
     2. Select "Use a LAN Cable" and follow the prompts to configure.

5. **Test the Connection:**
   Make sure your console is connected to the internet by running a network test or trying to connect to online services.

## Troubleshooting Tips
- If your console does not connect, double-check the sharing settings on your PC.
- Ensure that the Ethernet cable is properly connected and functioning.
- Restart both your PC and console if necessary.


## Connection Issues with Video Games and Sites
While using your PC as a hotspot via tethering, you may encounter issues where certain video games or websites report that you are offline, even though your internet connection is functioning properly. This can happen for several reasons, including:

1. **Network Restrictions**: Some games and services may impose restrictions on peer-to-peer (P2P) connections, which can prevent proper communication between your device and their servers.

2. **IP Address Configuration**: Tethering may assign a different IP address to your connection, which can lead to confusion in how certain applications perceive your online status.

3. **Firewall or NAT Issues**: The configuration of your network, particularly regarding firewalls or Network Address Translation (NAT), can also cause connectivity problems.

To resolve these issues, using a VPN can be very helpful. A VPN (Virtual Private Network) can:

- **Improve Connection Stability**: By masking your IP address and routing your traffic through a secure server, a VPN can bypass network restrictions and stabilize your connection.
- **Enhance Privacy and Security**: VPNs encrypt your internet traffic, making it more secure and private.

For reliable performance, I recommend using [Proton VPN](https://protonvpn.com/), known for its user-friendly interface and strong privacy policies. It supports P2P connections, making it an excellent choice for gamers and users of streaming services.


---

## Chapter 3: Windows Performance Optimization

This chapter covers advanced Windows optimizations to maximize your PdaNet USB tethering speed and reliability. These settings can significantly improve your experience, especially for gaming, streaming, and large downloads.

### Understanding PdaNet on Windows

When you connect via PdaNet USB tethering, Windows creates a virtual network adapter called **"PdaNet Broadband Adapter"**. This adapter appears as an Ethernet connection to Windows, typically showing a 1 Gbps link speed (this is the virtual link speed, not your actual mobile data speed).

**Key Network Details:**
- **Adapter Name:** PdaNet Broadband Connection
- **Interface Type:** Virtual Ethernet (Broadband Adapter)
- **IP Range:** Typically 10.1.19.x (DHCP from PdaNet)
- **Gateway:** 10.1.19.1 (your phone)

You can view your current configuration by opening PowerShell and running:
```powershell
ipconfig /all
```

Or for detailed adapter info:
```powershell
Get-NetAdapter | Format-Table Name, InterfaceDescription, Status, LinkSpeed -AutoSize
```

---

### Critical: Disable USB Selective Suspend

**This is the single most important optimization for USB tethering.**

Windows has a power-saving feature called "USB Selective Suspend" that allows the OS to put USB ports into a low-power state when not actively transferring data. While this saves battery, it causes major problems for tethering:

- **Intermittent disconnections**
- **Latency spikes** (ping jumps from 50ms to 500ms+)
- **Speed throttling** during idle periods
- **Connection drops** when resuming from suspend

#### How to Disable USB Selective Suspend

**Method 1: Via Power Options (GUI)**
1. Press `Win + R`, type `powercfg.cpl`, press Enter
2. Click "Change plan settings" next to your active plan
3. Click "Change advanced power settings"
4. Expand "USB settings" > "USB selective suspend setting"
5. Set both "On battery" and "Plugged in" to **Disabled**
6. Click Apply > OK

**Method 2: Via PowerShell (Recommended)**
```powershell
# Run as Administrator
powercfg /SETACVALUEINDEX SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0
powercfg /SETDCVALUEINDEX SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0
powercfg /SETACTIVE SCHEME_CURRENT
```

**Verify the change:**
```powershell
powercfg /query SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3
```
You should see `Current AC Power Setting Index: 0x00000000` (Disabled).

---

### Network Interface Priority (Metric)

Windows uses "interface metrics" to determine which network adapter to use when multiple are available. A **lower metric = higher priority**. By default, PdaNet may have the same metric as Wi-Fi (25), which can cause routing conflicts.

#### Check Current Metrics
```powershell
Get-NetIPInterface | Format-Table InterfaceAlias, InterfaceMetric, ConnectionState, AddressFamily -AutoSize
```

#### Set PdaNet as Highest Priority
```powershell
# Run as Administrator - Sets metric to 5 (very high priority)
Set-NetIPInterface -InterfaceAlias "PdaNet Broadband Connection" -InterfaceMetric 5
```

**Recommended Metrics:**
| Adapter | Metric | Priority |
|---------|--------|----------|
| PdaNet Broadband Connection | 5 | Highest |
| Ethernet (when available) | 15 | High |
| Wi-Fi | 25 | Medium |
| Bluetooth PAN | 65 | Low |

---

### Power Plan Configuration

For optimal tethering performance, use the **High Performance** power plan. This prevents CPU throttling and ensures maximum USB controller performance.

#### Check Current Power Plan
```powershell
powercfg /getactivescheme
```

#### Switch to High Performance
```powershell
# Run as Administrator
powercfg /setactive 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
```

#### Recommended Power Settings for Tethering

| Setting | Value | Why |
|---------|-------|-----|
| USB Selective Suspend | Disabled | Prevents USB throttling |
| PCI Express Link State | Off | Prevents adapter sleep |
| Processor Min State | 100% (AC) | Maximum CPU performance |
| Wireless Adapter Power | Maximum Performance | If using Wi-Fi hotspot |

---

### TCP/IP Optimization Settings

Windows has several TCP/IP settings that affect network performance. Here are the optimal settings for mobile tethering:

#### View Current TCP Settings
```powershell
netsh int tcp show global
netsh int tcp show supplemental
```

#### Recommended TCP Global Settings

| Setting | Optimal Value | Description |
|---------|---------------|-------------|
| Receive-Side Scaling | Enabled | Distributes network processing across CPU cores |
| Receive Window Auto-Tuning | Experimental | Aggressive buffer sizing for high latency |
| ECN Capability | Enabled | Explicit Congestion Notification |
| RFC 1323 Timestamps | Enabled | Better RTT measurement |
| Fast Open | Enabled | Reduces connection latency |
| Congestion Control | CTCP or CUBIC | Modern congestion algorithms |

#### Apply Optimal TCP Settings
```powershell
# Run as Administrator
netsh int tcp set global autotuninglevel=experimental
netsh int tcp set global ecncapability=enabled
netsh int tcp set global timestamps=enabled
netsh int tcp set global fastopen=enabled
netsh int tcp set global rss=enabled
```

**Note:** "Experimental" auto-tuning is more aggressive and works well for high-latency mobile connections. If you experience issues, you can set it back to "normal":
```powershell
netsh int tcp set global autotuninglevel=normal
```

#### View Network Offload Settings
```powershell
Get-NetOffloadGlobalSetting
```

Ensure these are enabled for best performance:
- **ReceiveSideScaling:** Enabled
- **ReceiveSegmentCoalescing:** Enabled
- **TaskOffload:** Enabled

---

### DNS Configuration

Fast DNS resolution improves perceived speed, especially for web browsing. Mobile carriers often have slow DNS servers.

#### Recommended DNS Servers

| Provider | Primary | Secondary | Notes |
|----------|---------|-----------|-------|
| Cloudflare | 1.1.1.1 | 1.0.0.1 | Fastest, privacy-focused |
| Google | 8.8.8.8 | 8.8.4.4 | Reliable, global |
| Quad9 | 9.9.9.9 | 149.112.112.112 | Security-focused, blocks malware |

#### Set DNS via PowerShell
```powershell
# Run as Administrator
Set-DnsClientServerAddress -InterfaceAlias "PdaNet Broadband Connection" -ServerAddresses ("1.1.1.1","1.0.0.1","8.8.8.8")
```

#### Test DNS Speed
```powershell
(Measure-Command { Resolve-DnsName google.com }).TotalMilliseconds
```
A good result is under 100ms. Mobile tethering typically sees 200-500ms due to cellular latency.

#### Flush DNS Cache
If you experience DNS issues after changing settings:
```powershell
ipconfig /flushdns
```

---

### Verifying Your Optimized Configuration

After applying optimizations, verify everything is configured correctly:

#### Complete Status Check Script
```powershell
Write-Host "=== PdaNet Optimization Status ===" -ForegroundColor Cyan

# Check adapter status
Write-Host "`n[Adapter Status]" -ForegroundColor Yellow
Get-NetAdapter -Name "PdaNet*" | Format-Table Name, Status, LinkSpeed -AutoSize

# Check interface metrics
Write-Host "[Interface Metrics]" -ForegroundColor Yellow
Get-NetIPInterface -InterfaceAlias "PdaNet*" | Format-Table InterfaceAlias, AddressFamily, InterfaceMetric -AutoSize

# Check USB suspend
Write-Host "[USB Selective Suspend]" -ForegroundColor Yellow
$usb = powercfg /query SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226
if ($usb -match "0x00000000") { Write-Host "  Status: DISABLED (Good)" -ForegroundColor Green }
else { Write-Host "  Status: ENABLED (Bad - disable this!)" -ForegroundColor Red }

# Check TCP settings
Write-Host "`n[TCP Settings]" -ForegroundColor Yellow
netsh int tcp show global | Select-String "Auto-Tuning|ECN|Timestamps|Fast Open"

# Check DNS
Write-Host "`n[DNS Servers]" -ForegroundColor Yellow
Get-DnsClientServerAddress -InterfaceAlias "PdaNet*" -AddressFamily IPv4 | Format-Table InterfaceAlias, ServerAddresses -AutoSize

# Test connectivity
Write-Host "`n[Connectivity Test]" -ForegroundColor Yellow
$tcp = Test-NetConnection -ComputerName google.com -Port 443 -WarningAction SilentlyContinue
Write-Host "  TCP to Google: $($tcp.TcpTestSucceeded)"

Write-Host "`n=== Check Complete ===" -ForegroundColor Cyan
```

---

### Quick Optimization Checklist

Use this checklist to quickly optimize a fresh Windows installation for PdaNet:

- [ ] **Install PdaNet** desktop client and phone app
- [ ] **Install correct USB drivers** for your phone (OEM + ADB)
- [ ] **Set Power Plan** to High Performance
- [ ] **Disable USB Selective Suspend** (both AC and DC)
- [ ] **Set PdaNet interface metric** to 5 (lowest = highest priority)
- [ ] **Configure DNS** to Cloudflare (1.1.1.1, 1.0.0.1)
- [ ] **Enable TCP optimizations** (experimental auto-tuning, ECN, timestamps)
- [ ] **Verify no QoS throttling** policies are active
- [ ] **Test connection** with speed test and latency check

#### One-Liner Full Optimization (Run as Administrator)
```powershell
# Disable USB suspend, set metric, configure DNS
powercfg /SETACVALUEINDEX SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0; powercfg /SETDCVALUEINDEX SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0; powercfg /SETACTIVE SCHEME_CURRENT; Set-NetIPInterface -InterfaceAlias "PdaNet Broadband Connection" -InterfaceMetric 5; Set-DnsClientServerAddress -InterfaceAlias "PdaNet Broadband Connection" -ServerAddresses ("1.1.1.1","1.0.0.1","8.8.8.8")
```

---

### Optimized State Reference

After applying all optimizations, your system should have these settings:

| Setting | Optimized Value |
|---------|-----------------|
| Power Plan | High Performance |
| USB Selective Suspend | Disabled (AC & DC) |
| PdaNet Interface Metric | 5 |
| TCP Auto-Tuning | Experimental |
| TCP ECN | Enabled |
| TCP Timestamps | Enabled |
| TCP Fast Open | Enabled |
| Receive-Side Scaling | Enabled |
| DNS Servers | 1.1.1.1, 1.0.0.1, 8.8.8.8 |
| QoS Throttling | None |

---

### Performance Expectations

With USB tethering, your speeds depend on your mobile carrier and signal strength. Here's what to expect:

| Metric | Typical Range | Notes |
|--------|---------------|-------|
| Download Speed | 10-100+ Mbps | Depends on 4G/5G signal |
| Upload Speed | 5-30 Mbps | Usually lower than download |
| Latency (Ping) | 30-100ms | Higher than wired broadband |
| DNS Resolution | 200-500ms | Mobile adds latency |
| Jitter | 10-50ms | Variable due to cellular |

**Tips for Best Performance:**
- Keep your phone plugged into a USB 3.0 port (blue port)
- Use a high-quality USB cable (preferably the one that came with your phone)
- Position your phone where it has the best cellular signal
- Close unnecessary apps on your phone that may use data
- Avoid using your phone for other tasks while tethering

---

By following these instructions, you can successfully share your tethered internet connection with other devices through a hotspot or an Ethernet connection!
