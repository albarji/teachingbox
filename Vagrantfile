VAGRANTFILE_API_VERSION = "2"

$conda_installation = <<SCRIPT
curl https://repo.continuum.io/archive/Anaconda3-4.0.0-Linux-x86_64.sh -o anaconda.sh || exit 1;
bash anaconda.sh -b || exit 1;
grep -q anaconda ~/.bashrc;
if [[ ${?} -ne 0 ]]; then
    echo "export PATH=\"${HOME}/anaconda3/bin:\${PATH}\"" >> ~/.bashrc
fi
source ~/.bashrc
rm anaconda.sh || exit 1;
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "ubuntu/wily64"

    # Display the VirtualBox GUI when booting the machine
    config.vm.provider "virtualbox" do |vb|
        vb.gui = true
    end

    config.vm.provider "virtualbox" do |v|
        v.memory = 4096
        v.cpus = 2
    end

    # Install xfce and virtualbox additions
    config.vm.provision "shell", inline: "sudo apt-get update"
    config.vm.provision "shell", inline: "sudo apt-get install -y xfce4 virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11"
    # Permit anyone to start the GUI
    config.vm.provision "shell", inline: "sudo sed -i 's/allowed_users=.*$/allowed_users=anybody/' /etc/X11/Xwrapper.config"
    # Run GUI from the start
    config.vm.provision "shell", inline: "echo '[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && exec startx' > /home/vagrant/.bash_profile"

    # Install necessary system software
    config.vm.provision "shell", inline: "sudo apt-get install -y firefox curl file-roller evince"

    # Conda installation, with necessary packages
    config.vm.provision "shell", inline: $conda_installation, privileged: false

    # Install other required conda packages
    config.vm.provision "shell", inline: "/home/vagrant/anaconda3/bin/conda install -y seaborn", privileged: false

    # Install pip packages (not available in conda)
    config.vm.provision "shell", inline: "/home/vagrant/anaconda3/bin/pip install keras", privileged: false
end
