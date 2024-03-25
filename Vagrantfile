Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "3072"
    vb.cpus = 2
  end

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    # Comandi per aprire la porta 8080 nel firewall
    sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent
    sudo firewall-cmd --reload

    # Comandi per installare Docker e Minikube
    sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    sudo dnf install docker-ce --nobest -y
    sudo systemctl start docker
    sudo systemctl enable docker
    sudo usermod -aG docker vagrant && newgrp docker
    sudo chmod 666 /var/run/docker.sock
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x kubectl
    sudo mv kubectl /usr/local/bin/
    
    # Avvia Minikube e abilita gli addon
    /usr/local/bin/minikube start
    /usr/local/bin/minikube addons enable metrics-server
    /usr/local/bin/minikube addons enable dashboard
    
    sleep 60

    # Inoltro della porta per accedere al dashboard di Kubernetes
    /usr/local/bin/kubectl --namespace=kubernetes-dashboard port-forward --address 0.0.0.0 svc/kubernetes-dashboard 8080:80
  SHELL
end
