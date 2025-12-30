# KVM-examples



qemu-img create -f qcow2 -F qcow2 \
  -b /home/ubuntu/cloud-native/noble-server-cloudimg-amd64.img \
  /var/lib/libvirt/images/myvm.qcow2 20G
