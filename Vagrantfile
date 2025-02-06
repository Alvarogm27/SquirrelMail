# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.define "mail" do |mail|
    mail.vm.hostname = "mail"
    mail.vm.network "private_network", ip: "192.168.57.10"
    mail.vm.provision "shell", inline: <<-SHELL
      apt update && apt upgrade -y
      #DNS
      apt install bind9 -y 
      cp /vagrant/dns/named.conf.local /etc/bind/
      cp /vagrant/dns/db.aula.izv /etc/bind/
      cp /vagrant/dns/db.57.168.192 /etc/bind/
      cp /vagrant/dns/named.conf.options /etc/bind/

      #webmail
      cp /vagrant/webmail/hostname /etc/hostname
      cp /vagrant/webmail/hosts /etc/hosts
      cp /vagrant/webmail/resolv.conf /etc/resolv.conf

      #Dovecot
      apt install dovecot-core dovecot-imap dovecot-pop3 -y


    SHELL
  end
end
