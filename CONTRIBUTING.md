# Contribuindo para o Projeto Terraform-Libvirt-KVM

Primeiramente, obrigado por se interessar em contribuir! Este projeto visa facilitar o provisionamento de infraestrutura local de forma ágil e segura.

## 🛠 Pré-requisitos para Desenvolvimento

Para garantir que suas alterações funcionem, seu ambiente local deve ter:
*   **Terraform** (v1.0+)
*   **Libvirt** instalado e o serviço `libvirtd` rodando.
*   **QEMU/KVM** configurado.
*   Plugin do **Terraform Provider Libvirt** devidamente instalado.

## 🚀 Como Contribuir

1.  Faça um **Fork** do projeto.
2.  Crie uma **Branch** para sua modificação: `git checkout -b feature/minha-melhoria`.
3.  Execute o comando de formatação: `terraform fmt`. **Não aceitamos PRs com código desformatado.**
4.  Valide as alterações: `terraform validate`.
5.  Se possível, realize um teste real: `terraform apply` (cuidado com os recursos do seu host).
6.  Dê um **Push** para a sua branch e abra um **Pull Request**.

## 📏 Padrões de Código

*   **Variáveis:** Devem ter sempre um campo `description` e, se apropriado, um `default`.
*   **Outputs:** Sempre defina outputs para informações úteis (como IPs das VMs).
*   **README:** Se adicionar uma nova funcionalidade ou variável, atualize os READMEs necessários.

## 🛡 Segurança
Nunca faça commit de arquivos `.tfvars` que contenham dados sensíveis ou chaves SSH privadas. Utilize o arquivo `.gitignore` já presente no projeto.

## 💬 Comunidade e Conduta
Ao interagir neste projeto, siga as normas de respeito e colaboração técnica.
