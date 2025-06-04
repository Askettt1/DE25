# DE25

### https://github.com/pizzamoya/demo25
### https://disk.yandex.ru/d/ZQvka2pAcGDlsA
### http://24kiberpride-support.ru/calc

####################################### </br>
Последовательность 1 модуль: </br>
Имена, часовой пояс </br>
isp, </br>
ip-add,</br>
на роутерах dhcp, OSPF, nat, тунель </br>
Пользователи, ssh, </br>
Dns </br>
Последовательность 2 модуль: </br>
</br>
Isp: </br>
Скопировать ens18 - ens19 cp -r ens18/ ens19 </br>
Options - bootproto: static добавить DISABLED=no ONBOOT=yes </br>
Выставить ipv4addres </br>
Скопировать ens19 в ens20 и поменять адрес. </br>
/etc/net/sysctl.conf </br>
sysctl -w net.ipv4.ip_forward=1 </br>
Iptables -A POSTROUTING -t nat  -o ens18 -j MASQUERADE </br>
Iptables -t nat -L </br>
Iptables-save > /etc/sysconfig/iptables </br>
Rtrs </br>
</br>
ISp-Hq 172.16.4.0/28 </br>
Hq 192.168.100.1/26, 192.168.100.65/28, 192.168.100.81/29 </br>
Hqsrv 192.168.100.62 </br>
</br>
Isp-br 172.16.5.0/28 </br> 
Br 192.168.200.1/27 </br>
Brsrv 192.168.200.30 </br>
</br>
 для OSPF </br>
int tunnel.0  </br>
IP mtu 1400 </br>
ip ospf authetication message-digest </br>
ip ospf message-digest-key 1 md5 P@ssword </br>
</br>
IP nat pool Hq 192.168.100.1-192.168.100.87 </br>
ip nat source dynamic inside-to-outside pool Hq overload int int1 </br>
</br>
ip pool Hq 192.168.100.66-192.168.100.78 </br>
Dhcp server 1 </br>
Pool Hq 1 </br>
Mask 28 </br>
Gateway 192.168.100.65 </br>
Dns 192.168.100.62 </br>
Domain-name au-team.irpo </br>
Int3 </br>
DHCP-server 1 </br>
</br>
useradd sshuser -u 1010 </br>
/etc/openssh/sshd_config port 2024 AllowUsers sshuser MaxAuthTries 2 Banner /etc/openssh/banner </br>
</br>
rm -f /etc/samba/smb.conf </br>
rm -rf /var/lib/samba </br>
rm -rf /var/cache/samba </br>
mkdir -p /var/lib/samba/sysvol </br>
Start samba </br>
cp /var/lib/samba/Private/krb5.conf /etc/krb5.conf </br>
Restart samba </br>

