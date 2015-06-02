all:
	@echo Choose you bitch

reload:
	sudo cp dnsmasq.conf /etc/dnsmasq.conf
	sudo systemctl stop dnsmasq
	sudo systemctl start dnsmasq
	sudo systemctl status dnsmasq

script:
	make -C ./ipxe/src bin/undionly.kpxe EMBED=../../test.ipxe
	cp ./ipxe/src/bin/undionly.kpxe ./undionly.kpxe

apply:
	cp ./undionly.kpxe ../../tinykore/iso/
