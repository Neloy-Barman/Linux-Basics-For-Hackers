**Note:** _Currently we have `password.lst` instead of `passwords.lst`._

1. `ifconfig`
2. `sudo ifconfig eth0 192.168.1.1`
3. 
   1. `sudo ifconfig eth0 down`
   2. `sudo ifconfig eth0 hw ether 00:11:22:33:44:55`
   3. `sudo ifconfig eth0 up`

    **Note:**_Changing MAC ADDRESS totally disables the networking. If you do it, you need to shut down and run the VM Box again. None of the method actually works. I tested and that's the solve for now._
4. `iwconfig`
5. `sudo dhclient eth0`
6. 
   1. `dig google.com ns
   2. `dig google.com mx`
7. 
   1. `sudo l3afpad /etc/resolv.conf`
   2. Add google ns found from dig command
   3. Save it and check the change
   4. `cat /etc/resolv.conf`
