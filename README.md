
# Infraestrutura de Laboratório com Terraform + Libvirt

> Projeto de suporte ao TCC *"Automação do Gerenciamento de Servidores com Ansible"*  
> **FATEC Osasco** | **Autor:** Marcos Donato  
> **Ano:** 2026

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Terraform](https://img.shields.io/badge/Terraform-1.14+-purple.svg)](https://www.terraform.io/)
[![Provider](https://img.shields.io/badge/Provider-0.9.1-orange.svg)](https://registry.terraform.io/providers/dmacvicar/libvirt/latest)

## Sobre o Projeto

Repositório com a infraestrutura como código (IaC) para provisionar o ambiente de laboratório utilizado no TCC.  
Cria máquinas virtuais **Linux (Ubuntu/Rocky), Windows Server e VyOS** com redes IPv4/IPv6, Cloud-init e módulos reutilizáveis via Terraform + Libvirt/KVM.

### Destaques
- ✅ Provisionamento declarativo de VMs com Libvirt/KVM
- ✅ Suporte a Cloud-init (Linux/VyOS) e drivers VirtIO (Windows)
- ✅ Redes isoladas com DHCP, NAT e dual-stack IPv4/IPv6
- ✅ Estrutura modular: `network`, `volume`, `cloudinit`, `domain_linux`, `domain_windows`
- ✅ Saída pronta para gerar inventário do Ansible (`provisioned_vms`)

## Pré-requisitos

- **Terraform/OpenTofu:** ≥ 1.14 / ≥ 1.11
- **Provider:** `dmacvicar/libvirt = 0.9.1`
- **Libvirt/KVM:** ≥ `libvirtd` ativo no host
- **Acesso SSH** aos hosts gerenciados (Linux) ou **WinRM** (Windows)
- **Privilégios** sudo (Linux) / Admin (Windows)

## 📁 Estrutura do Projeto

```bash
TCC_terraform/
├── modules/
│   ├── orchestration      # Orquestrador central
│   ├── network            # Redes Libvirt (IPv4/IPv6, DHCP, NAT)
│   ├── volume             # Volumes de disco (backing store)
│   ├── cloudinit          # ISOs de Cloud-init (Linux/VyOS)
│   ├── domain_linux       # Domínios KVM para Linux/VyOS
│   └── domain_windows     # Domínios KVM para Windows
│
└── environments/
    └── lab-ansible/               # Ambiente de exemplo (laboratório)
        ├── *.auto.tfvars.exemplo
        └── README.md
```

## Integração com Ansible

Após o `apply`, a saída `provisioned_vms` fornece dados estruturados para gerar o inventário do Ansible:

```json
  "SdnsDMZ03" = {
    "current_memory" = 2048
    "disks" = [
      {
        "bootable" = true
        "size_gb" = 50
        "vol_name" = "SdnsDMZ03-os"
      },
    ]
    "memory" = 2048
    "networks" = [
      {
        "dns_servers" = [
          "10.20.100.10",
          "10.20.200.10",
        ]
        "ipv4_address" = "10.20.200.10"
        "ipv4_gateway" = "10.20.200.254"
        "ipv4_prefix" = 24
        "name" = "dmz-net"
      },
    ]
    "os_type" = "linux"
    "running" = true
    "status" = "running"
    "vcpus" = 1
  }
```

> 💡 Dica: Use o script `ansible_project_v4.sh` do repositório [TCC_ansible](https://github.com/donato-marcos/TCC_ansible) para criar a estrutura de playbooks compatível com as VMs provisionadas.

## 📚 Documentação dos Módulos

Cada módulo possui seu próprio `README.md` com entradas, saídas e exemplos:

* [`Terraform_README.md`](Terraform_README.md)

> 🎓 *Projeto desenvolvido como auxiliar do Trabalho de Conclusão de Curso em Redes de Computadores pela FATEC Osasco.*
