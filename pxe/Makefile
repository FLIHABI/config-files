all: script pxe

pxe:
	sudo umount -l /mnt/iso || /bin/true
	sudo mount -o loop,ro ../../tinykore/test.iso /mnt/iso/
	make reload
	darkhttpd /mnt/iso

reload:
	sudo cp dnsmasq.conf /etc/dnsmasq.conf
	sudo systemctl stop dnsmasq
	sudo systemctl start dnsmasq
	sudo systemctl status dnsmasq

script:
	make -C ./ipxe/src bin/undionly.kpxe EMBED=../../test.ipxe DEBUG=apm
	cp ./ipxe/src/bin/undionly.kpxe ./undionly.kpxe
	cp ./undionly.kpxe ../../tinykore/iso/
	make -C ../../tinykore pack
