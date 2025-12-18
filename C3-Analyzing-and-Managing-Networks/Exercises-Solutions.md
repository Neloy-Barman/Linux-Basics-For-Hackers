**Note:** _Currently we have `password.lst` instead of `passwords.lst`._

1. 
    ```bash
        ifconfig
        iwconfig
    ```
2. 
    ```bash
        sudo ifconfig eth0 192.168.1.1
    ```
3. 
    ```bash
        sudo ifconfig eth0 down
        sudo ifconfig eth0 hw ether 00:11:22:33:44:55
        sudo ifconfig eth0 up
    ```
    **Note:**_Changing MAC ADDRESS totally disables the networking. If you do it, you need to shut down and run the VM Box again. None of the method actually works. I tested and that's the solve for now._
4. 
    ```bash
        iwconfig
    ```
5. 
    ```bash
        sudo dhclient eth0
    ```
6. 
    ```bash
        dig google.com ns
        dig google.com mx
    ```
7. 
    ```bash
        sudo l3afpad /etc/resolv.conf
    ```
    - Add google ns found from dig command
    - Save it and check the change
    ```bash
        cat /etc/resolv.conf
    ```
