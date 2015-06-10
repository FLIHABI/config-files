all: script apply
	make -C ../../tinykore pack
ifneq "$(df | grep /mnt/iso)" ""
	echo "Nothing to unmount"
else
	sudo umount -l /mnt/iso
endif
	sudo mount -o loop,ro ../../tinykore/test.iso /mnt/iso/
	make reload
	darkhttpd /mnt/iso

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
