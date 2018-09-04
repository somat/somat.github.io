```
qemu-img create centos-minimal.img 10G

qemu-system-x86_64 -enable-kvm -m 1024 -hda ./centos-minimal.img -vnc :7

virsh attach-interface --domain <vm-name> --type bridge --source br0 --model virtio --config --live

virt-install --connect qemu:///system -n <vm-name> -r 1024 --vcpus=1 \
--disk /var/lib/libvirt/images/<vm-name>.img,device=disk,bus=virtio,size=50 \
-c /var/lib/libvirt/images/CentOS-7-x86_64-Minimal-1708.iso --vnc --noautoconsole \
--os-type linux --os-variant rhel7 --accelerate --network=bridge:br0 --hvm
```
