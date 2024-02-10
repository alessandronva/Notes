# Creating DNS entry for an IP

* Open a terminal on your Linux system.
*   Open the `/etc/hosts` file using a text editor with administrative privileges. You can use a command-line text editor like `nano` or `vi`, or a graphical text editor like `gedit` or `kate`. For example, to open the file with `nano`, you can use the following command:

    ```
    bash
    ```
* ```bash
  sudo nano /etc/hosts
  ```
*   Add a new line at the end of the file in the following format:

    ```
    ```

```
IP_ADDRESS    CUSTOM_DNS_NAME
```

Replace `IP_ADDRESS` with the IP address you want to map the custom DNS name to, and replace `CUSTOM_DNS_NAME` with the desired DNS name.

For example:

```
lua
```

* ```lua
  192.168.1.100    mycustomdnsname.local
  ```
* Save the changes and exit the text editor.
*   To make sure the changes take effect, you can flush the DNS cache on your system. The command for flushing the DNS cache can vary depending on your Linux distribution. For example, on Ubuntu, you can use the following command:

    ```
    ```

1. ```
   sudo systemctl restart systemd-resolved
   ```

That's it! Now you should be able to use the custom DNS name (`mycustomdnsname.local` in the example) to refer to the specified IP address (`192.168.1.100` in the example) on your Linux system.
