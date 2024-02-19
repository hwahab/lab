# lab


cat <<EOF > /etc/init.d/pjd_fake_lo
#!/bin/sh
## This service was created by plafonta
. /etc/init.d/functions
case "\$1" in
start)
ip link add name loop1 type dummy; if [ \$? -gt 0 ]; then exit \$?; fi
ip addr add 10.0.0.1/32 dev loop1; if [ \$? -gt 0 ]; then exit \$?; fi
ip link set loop1 up; if [ \$? -gt 0 ]; then exit \\$?; fi ;;
stop) ip link del dev loop1; if [ \$? -gt 0 ]; then exit \$?; fi ;;
restart|reload) \$0 stop; sleep 1; \$0 start; exit \$? ;;
*) echo "Usage: \$0 {start|stop|restart}"; exit 1; esac; exit 0
EOF
 
chmod +x /etc/init.d/pjd_fake_lo
for i in {2..5}; do ln -s /etc/init.d/pjd_fake_lo /etc/rc$i.d/S20pjd_fake_lo; done
service pjd_fake_lo start



Gateway:
cplic put 10.0.0.1 07Mar2024 arXZ6cReQ-EJ3eucZHX-YUrQvNdqg-o4dub47oc cpsg-c-8-u cpsb-fw cpsb-vpn cpsb-adn cpsb-accl cpsb-ipsa cpsb-dlp cpsb-sslvpn-50 cpsb-ia cpsg-vsx-25s cpsb-swb cpsb-ips cpsb-aspm cpsb-urlf cpsb-av cpsb-apcl cpsb-abot-l cpsb-ctnt CK-8BA34EDBD388

Management:
cplic put 10.0.0.1 07Mar2024 aeLvi7aoz-EyQVZtdHJ-7s2dMbjUM-ssjpz2sBe cpsm-c-u cpsb-adn-m cpsb-accl-m cpsb-npm cpsb-epm cpsb-logs cpsb-prvs cpsb-udir cpsb-mntr cpsb-wkfl-100 cpsb-ws cpsb-rprt-10 cpsb-mptl cpsb-evcr-10 cpvp-snx-25-ngx cpvp-snx-25-ngx cpsb-swb cpsb-comp-150 CK-8BA34EDBD388
