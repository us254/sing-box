To stop, remove the current sing-box binary, and install the version you built from source on Ubuntu, you can follow these steps:

1. Stop the sing-box service:
   ```
   sudo systemctl stop sing-box
   ```

2. Find the current sing-box executable:
   ```
   find / -name "sing-box" -type f 2>/dev/null
   ```
   This command will search for the sing-box executable file system-wide and display its location.

3. Remove the current sing-box executable:
   ```
   sudo rm /usr/bin/sing-box
   ```
   Replace `/path/to/sing-box` with the actual path of the sing-box executable found in step 2.

4. Uninstall the sing-box package (if installed via package manager):
   ```
   sudo dpkg --purge sing-box
   ```
   This command will remove the sing-box package and its associated files. If you installed sing-box using a different method, you may need to adjust this step accordingly.

5. Copy the built sing-box binary to the desired location:
   ```
   sudo cp -f /path/to/built/sing-box /usr/local/bin/
   ```
   Replace `/path/to/built/sing-box` with the actual path to the sing-box binary you built from source.

6. Set the appropriate permissions for the sing-box binary:
   ```
   sudo chmod +x /usr/local/bin/sing-box
   ```

7. Update the sing-box service file (if necessary):
   ```
   sudo nano /etc/systemd/system/sing-box.service
   ```
   In the service file, update the `ExecStart` line to point to the new sing-box binary location:
   ```
   ExecStart=/usr/local/bin/sing-box run
   ```
   Save the changes and exit the text editor.

8. Reload the systemd configuration:
   ```
   sudo systemctl daemon-reload
   ```

9. Start the sing-box service:
   ```
   sudo systemctl start sing-box
   ```

10. Verify the sing-box version:
    ```
    sing-box version
    ```
    This command should display the version information of the sing-box binary you built from source.

After following these steps, the current sing-box binary should be removed, and the version you built from source should be installed and running on your Ubuntu system.

Note: Make sure to replace `/path/to/built/sing-box` with the actual path to the sing-box binary you built from source, and adjust the steps according to your specific setup and configuration.
