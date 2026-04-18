
# Política de Segurança

## Versões Suportadas
Atualmente, fornecemos atualizações de segurança para as seguintes versões:


| Versão | Suportada          |
| ------- | ------------------ |
| 1.0.x   | ✅ Sim              |
| < 1.0   | ❌ Não              |

## Reportando uma Vulnerabilidade
A segurança deste projeto é levada a sério. Se você encontrar uma vulnerabilidade, por favor, **não abra uma Issue pública**. 

Em vez disso, siga os passos abaixo:
1. Envie um e-mail para **[SEU-EMAIL-AQUI]** com os detalhes técnicos.
2. Descreva o impacto potencial e como reproduzir o problema.
3. Você receberá uma resposta em até 48 horas confirmando o recebimento.

## Boas Práticas de Uso
Como este projeto lida com provisionamento de infraestrutura local:
- Nunca faça commit de arquivos `.tfstate` ou `.tfvars` que contenham segredos.
- Certifique-se de que o usuário que executa o Terraform tenha apenas as permissões necessárias no Libvirt.
