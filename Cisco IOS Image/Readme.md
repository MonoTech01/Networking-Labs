# CCNA Labs: Upgrading Cisco IOS via TFTP 🚀  

This lab demonstrates how to **upgrade a Cisco IOS image** using a **TFTP (Trivial File Transfer Protocol) server**. Keeping network devices up to date is essential for **security, performance, and new feature support**.  

## 🔹 Steps Covered:  
1. **Check Current IOS Version** – Using `show version` to verify the existing image  
2. **Backup Existing IOS Image** – Copying the current IOS image to the TFTP server  
3. **Transfer New IOS Image** – Using `copy tftp: flash:` to upgrade the IOS  
4. **Verify & Boot** – Setting the correct boot image and reloading the device  
5. **Confirm Upgrade** – Using `show version` to ensure the upgrade was successful  

## 🛠️ Skills Developed:  
✔ Configuring and using a **TFTP server** for IOS upgrades  
✔ Backing up and restoring **Cisco IOS images**  
✔ Ensuring **network device stability & security** with updated software  
✔ Troubleshooting **TFTP transfer issues** and boot failures  
