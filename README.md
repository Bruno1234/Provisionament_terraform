# Projeto 

Este projeto implementa uma infraestrutura virtual automatizada utilizando ```Terraform```, ```Libvirt/KVM``` e ```Cloud-Init```. O objetivo é criar um ambiente com duas máquinas virtuais que simulam uma comunicação em rede via ```DHCP```, demonstrando conceitos de ```Infraestrutura como Código (IaC)``` e provisionamento local.

# Componentes Principais
  -  Terraform: Ferramenta principal para orquestração da infraestrutura     (discos, rede, VMs).\  
  -  Libvirt/KVM: Hipervisor utilizado para virtualização local.\
  -  Cloud-Init: Utilizado para configuração automatizada do sistema nas   VMs durante o boot inicial.

# Máquinas Virtuais Criadas 

**dhcp-server**
  - IP estático:** ```10.0.0.2 ```\
  - Serviço: ```isc-dhcp-server```\
  - Distribui IPs de ```10.0.0.10 a 10.0.0.15```\
  - Scripts automatizados para instalação e configuração

**dhcp-client**
 - Recebe IP via DHCP (cliente)\
 - Interface configurada automaticamente com ```dhclient```

# Rede Virtual
- Nome: ```gateway```
- Modo: NAT ```(virbr1)```
- IP do gateway:** ```10.0.0.1/24```
  
# Pre-requisitos

sudo apt update -y \
sudo apt upgrade -y \
  sudo apt install -y \
  qemu-kvm \
  libvirt-daemon-system \
  libvirt-clients \
  virtinst \
  bridge-utils \
  virt-manager \
  dnsmasq-base \
  net-tools \
  cloud-image-utils \
  genisoimage\
snap install terraform --classic

# Execução passo-passo:
```
sudo su
virsh net-define gateway.xml
virsh net-start gateway
virsh net-autostart gateway
sudo virsh pool-define-as default dir - - - - "/var/lib/libvirt/images"
sudo virsh pool-build default
sudo virsh pool-start default
sudo virsh pool-autostart default
terraform init
terraform apply
```

# Equipe:
- Luis Eduardo
- Bruno Eduardo
- Joao Otavio

````mermaid
block-beta
columns 1
  db(("DB"))
  blockArrowId6<["&nbsp;&nbsp;&nbsp;"]>(down)
  block:ID
    A
    B["A wide one in the middle"]
    C
  end
  space
  D
  ID --> D
  C --> D
  style B fill:#969,stroke:#333,stroke-width:4px
```
