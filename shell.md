#git
sudo apt-get update
sudo apt-get install git

#zshell
sudo apt-get install zsh
curl -L http://install.ohmyz.sh | sh
chsh -s /bin/zsh
sudo shutdown -r 0

#openssh
sudo apt-get install openssh-client
sudo apt-get install openssh-server
ssh-keygen
chmod 600 .ssh/authorized_keys
ssh-copy-id username@remotehost

#ansible
sudo apt-get -y install python-pip
sudo apt-add-repository ppa:ansible/ansible -y
sudo apt-get update
sudo apt-get install ansible