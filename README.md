# KVM-examples



qemu-img create -f qcow2 -F qcow2 \
  -b /home/ubuntu/cloud-native/noble-server-cloudimg-amd64.img \
  /var/lib/libvirt/images/myvm.qcow2 20G

cloud-localds /var/lib/libvirt/images/seed.iso user-data.yaml
  
virt-install \
  --name myvm \
  --ram 2048 --vcpus 2 \
  --disk path=/var/lib/libvirt/images/myvm.qcow2,bus=virtio \
  --disk path=/var/lib/libvirt/images/seed.iso,device=cdrom \
  --os-variant ubuntu24.04 \
  --network network=default,model=virtio \
  --graphics vnc \
  --import \
  --boot hd,cdrom,menu=on  
