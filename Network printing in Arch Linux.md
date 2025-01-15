## Network Printing in Arch Linux


    sudo pacman -S cups cups-browsed avahi nss-mdns

Edit /etc/nsswitch.conf and change the line:

	hosts: mymachines resolve [!UNAVAIL=return] files myhostname dns

into

	hosts: mymachines mdns_minimal [NOTFOUND=return] resolve [!UNAVAIL=return] files myhostname dns

Then enable services

	sudo systemctl enable --now avahi-daemon
	sudo systemctl enable --now cups
	sudo systemctl enable --now cups


