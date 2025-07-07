# Projeto 

- Estrutura Terraform que provisiona localmente duas VMs usando KVM/libvirt, conectadas a uma rede virtual com DHCP, em que:
- Uma VM atua como servidor DHCP
- Outra como cliente DHCP
- Um roteador/gateway opcional pode ser configurado (simples forwarding + NAT)
  
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
