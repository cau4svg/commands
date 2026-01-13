# 🛠️ DevOps Infrastructure Command Cheat Sheet

Checklist completo de comandos essenciais para um DevOps responsável pela infraestrutura
(Linux, Containers, Redes, Segurança e Cloud).

------------------------------------------------------------

## 📌 1. Sistema Operacional (Linux)

Informações do sistema
```bash
uname -a
hostnamectl
uptime
lsb_release -a
arch
```

Usuários e permissões
```bash
useradd user
usermod -aG sudo user
userdel user
passwd user
groups user
id user
whoami
```

Permissões
```bash
chmod 755 file
chown user:group file
getfacl file
setfacl -m u:user:rwx file
```

------------------------------------------------------------

## ⚙️ 2. Processos e Performance
```bash
top
htop
atop
ps aux
pstree
kill PID
kill -9 PID
pkill process
uptime
free -h
vmstat
iostat
mpstat
```

------------------------------------------------------------

## 💾 3. Disco, Filesystem e LVM
```bash
df -h
du -sh *
lsblk
mount
umount
findmnt
```

Partições
```bash
fdisk -l
parted
mkfs.ext4 /dev/sdX
```

LVM
```bash
pvdisplay
vgdisplay
lvdisplay
lvcreate
lvextend
lvreduce
resize2fs
```

------------------------------------------------------------

## 🌐 4. Rede e Portas

Interfaces e rotas
```bash
ip a
ip r
ifconfig
route -n
```

Portas abertas e serviços escutando
```bash
ss -tulnp
netstat -tulnp
lsof -i -P -n
```

Testes de conectividade
```bash
ping
traceroute
mtr
curl
wget
nc
telnet
nmap
```

------------------------------------------------------------

## 🔥 5. Firewall
```bash
iptables
iptables -L -n -v
iptables-save
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -D INPUT -p tcp --dport 80 -j ACCEPT

firewalld
firewall-cmd --list-all
firewall-cmd --add-port=80/tcp --permanent
firewall-cmd --remove-port=80/tcp --permanent
firewall-cmd --reload

ufw
ufw status
ufw allow 22
ufw allow 80
ufw deny 23
ufw reload
```

------------------------------------------------------------

## 🧩 6. Systemd e Serviços
```bash
systemctl status service
systemctl start service
systemctl stop service
systemctl restart service
systemctl reload service
systemctl enable service
systemctl disable service
```
Logs
```bash
journalctl
journalctl -u service
journalctl -xe
journalctl --since today
journalctl --since "1 hour ago"
```

------------------------------------------------------------

## 🐳 7. Docker

Status
```bash
systemctl status docker
docker info
docker version
```

Containers
```bash
docker ps
docker ps -a
docker start container
docker stop container
docker restart container
docker rm container
```

Imagens
```bash
docker images
docker pull image
docker rmi image
docker image prune
```

Execução e logs
```bash
docker exec -it container bash
docker logs container
docker logs -f container
```

Docker Compose
```bash
docker-compose up -d
docker-compose down
docker-compose ps
docker-compose logs
```

------------------------------------------------------------

## 🚦 8. Nginx
```bash
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl reload nginx
```

Configuração
```bash
nginx -t
nginx -T
```

Logs
```bash
tail -f /var/log/nginx/access.log
tail -f /var/log/nginx/error.log
```

Portas usadas pelo nginx
```bash
ss -tulnp | grep nginx
```

------------------------------------------------------------

## 📜 9. Logs e Debug
```bash
journalctl
tail -f /var/log/syslog
tail -f /var/log/messages
grep "error" file
less file
awk '{print $1}' file
sed 's/foo/bar/g' file
```

------------------------------------------------------------

## 🔐 10. Segurança

SSH
```bash
ssh user@host
ssh-copy-id user@host
ssh-keygen
```

Auditoria
```bash
last
lastlog
faillog
who
w
```

SELinux
```bash
getenforce
setenforce 0
sestatus
semanage
restorecon
```

------------------------------------------------------------

## ☸️ 11. Kubernetes
```bash
kubectl get nodes
kubectl get pods
kubectl get svc
kubectl get deployments
kubectl describe pod
kubectl logs pod
kubectl exec -it pod -- bash
kubectl apply -f file.yaml
kubectl delete -f file.yaml
kubectl rollout status deployment
```

------------------------------------------------------------

## ☁️ 12. Cloud (AWS CLI)
```bash
aws configure
aws ec2 describe-instances
aws ec2 start-instances
aws ec2 stop-instances
aws s3 ls
aws s3 cp
aws logs tail
aws eks update-kubeconfig
```

------------------------------------------------------------

## 🧱 13. Infra as Code

Terraform
```bash
terraform init
terraform validate
terraform plan
terraform apply
terraform destroy
terraform state list
terraform state rm
```

Ansible
```bash
ansible all -m ping
ansible-playbook playbook.yml
ansible-inventory --list
ansible-vault encrypt file
ansible-vault decrypt file
```

------------------------------------------------------------

## 💽 14. Backup e Agendamento
```bash
rsync -avz source dest
scp file user@host:/path
tar -czvf backup.tar.gz dir
tar -xzvf backup.tar.gz
crontab -e
crontab -l
```

------------------------------------------------------------

## 🧰 15. Utilitários Indispensáveis
```bash
tmux
tmux new -s session
tmux attach -t session
screen
vim
nano
jq
yq
bash
zsh
```

------------------------------------------------------------
