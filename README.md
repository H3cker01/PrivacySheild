# PrivacySheild
Network Privacy Shield & DHCP Remover
A lightweight Windows utility designed to enhance local network privacy by removing your device from the router's DHCP client list and hiding your hostname from neighbors networks.
## 🛡️ Features
DHCP Client Removal: Automatically switches your connection from DHCP to a Static IP. This stops the router from logging your device in its "Active Leases" list.
Dynamic Gateway Detection: Automatically detects your router's IP address and configures your settings to match any network (192.168.0.1, 192.168.1.1, 10.0.0.1, etc.).
Hostname Anonymization: Renames your PC to a generic WORKSTATION-01 to prevent personal identification.
Network Stealth: Disables SMB/NetBIOS broadcasting so your PC doesn't show up in the "Network" folder of other computers on the same Wi-Fi.
## 🚀 How It Works
Stealth Mode: It runs net config server /hidden:yes to stop broadcasting your presence.
Identity Shift: It uses PowerShell to force a computer rename.
Static Assignment: It calculates a safe IP (ending in .50) based on your current gateway and applies it along with Google DNS (8.8.8.8).
## 📥 Installation & Usage
Download the PrivacyShield.exe from the Releases page.
Right-click and Run as Administrator (required to modify network stack).
Wait for the success message.
Restart your computer to finalize the name change and stealth settings.
## 🛠️ Technical Details
Language: Python 3.x / PowerShell
Permissions: Requires UAC Administrator privileges.
Compatibility: Windows 10 & 11.
## ⚠️ Disclaimer
This tool modifies network adapter settings. It is intended for privacy enthusiasts and home lab use. If you are on a strictly managed corporate network, consult your admin before use, as static IPs can cause conflicts if not managed correctly.
## 🔄 How to Revert Changes
If you need to switch back to standard network settings (e.g., for a corporate environment or troubleshooting), use the included RestoreDefaults.exe.
What the Restore Tool does:
Enables Network Discovery: Runs net config server /hidden:no so your PC is visible to others again.
Resets to DHCP: Switches your network adapter from a Static IP back to Automatic (DHCP) mode.
Resets DNS: Removes Google DNS and reverts to your router’s default DNS settings.
Renames PC: Sets the hostname to a standard DESKTOP-RESTORED format.
Note: Just like the main tool, a restart is required after running the restore utility to finalize the hostname change.
# 🆘 Emergency Recovery: Comms Recovery Tool
In the event that the network stack becomes corrupted or your connection is lost after using Privacy Shield or Restore Defaults, use the Privacy Shield Comms Recovery utility.
What the Recovery Tool does:
Automatic Wi-Fi Backup: Saves your Wi-Fi profiles/passwords before the reset.
Deep Stack Purge: Runs netcfg -d to physically uninstall and reinstall all network adapters.
Service Restoration: Re-enables critical services (WLAN/Wired AutoConfig) that may have been disabled.
Auto-Restore: Re-injects your saved Wi-Fi passwords automatically upon the first login after reboot.
Usage: Run PrivacyShieldCommsRecovery.exe as Administrator and Restart immediately when prompted.
