# Deploy SONARQUBE on Kubernetes with Persistent Storage

  On NFS server

    vim /etc/exports
      /sonarqube/mysql *(rw,sync,no_root_squash)
      /sonarqube/data *(rw,sync,no_root_squash)
      /sonarqube/extensions *(rw,sync,no_root_squash)

    sudo mkdir -p /sonarqube/mysql; sudo mkdir -p /sonarqube/data; sudo mkdir -p /sonarqube/extensions

    sudo chmod -R 755 /sonarqube

    sudo chown nfsnobody:nfsnobody /sonarqube -R

    systemctl restart rpcbind

    systemctl restart nfs-server

    systemctl restart nfs-lock

    systemctl restart nfs-idmap


  git clone https://github.com/M-Ayman/K8s-Sonar.git

  cd K8s-Sonar

  inside sonar-deployment.yaml and sonar-mysql-deployment.yaml

    Replace server: "" with server: "the ip of NFS Server"

  kubectl create -f .

  open the browser and hit any ip of worker node on port 30080

      Username: admin
      Password: admin
