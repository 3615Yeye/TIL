Source : https://github.com/foxlet/macOS-Simple-KVM/

The source is far more interesting than my quick setup guide for myself. 

``` bash
# Create a qemu directory in home and setup rights
sudo mkdir /home/qemu
sudo chown qemu:ronan /home/qemu
sudo chmod g+w /home/qemu

# Get the latest release
git clone https://github.com/foxlet/macOS-Simple-KVM.git
cd macOS-Simple-KVM

# Install dependencies
sudo dnf install qemu qemu-img python3 python3-pip

# To download Mojave installation image (for 32 bit apps)
./jumpstart.sh --mojave

# Creating the volume
qemu-img create -f qcow2 Mojave.qcow2 64G

# Add the  volume conf at the end of basic.sh
vim basic.sh
    -drive id=SystemDisk,if=none,file=Mojave.qcow2 \
    -device ide-hd,bus=sata.4,drive=SystemDisk \

# Add the config to the Virt-Manager GUI
sudo ./make.sh --add

# Open virt-manager and add the previsouly created disk disk to the MacOs Virtualized system

# On first boot remember to use Disk Utility and format the previsouly created disk with default parameters
# Otherwise no drive will be available to install
```

