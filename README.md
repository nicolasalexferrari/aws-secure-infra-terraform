# Infraestrutura Segura na AWS com Terraform

Template de infraestrutura como código (Terraform) que provisiona um bucket S3 
na AWS já nascendo com boas práticas de segurança em nuvem aplicadas: acesso 
público bloqueado, criptografia de dados em repouso e versionamento de arquivos.

## Práticas de segurança implementadas

- **Bloqueio de acesso público** — impede que o bucket seja exposto publicamente, 
  usando `aws_s3_bucket_public_access_block`.
- **Criptografia em repouso** — todos os arquivos são criptografados automaticamente 
  (AES256), usando `aws_s3_bucket_server_side_encryption_configuration`.
- **Versionamento** — mantém histórico de versões dos arquivos, permitindo recuperação 
  em caso de exclusão ou sobrescrita indevida, usando `aws_s3_bucket_versioning`.

## Por que este projeto não foi aplicado (`apply`) em uma conta AWS real

Este projeto foi desenvolvido e validado sem uma conta AWS ativa, por limitação 
de cartão de crédito internacional no momento do desenvolvimento. Por isso, o 
projeto foi levado até o limite possível sem custo: código escrito, validado 
sintaticamente (`terraform validate`) e testado até a etapa de `terraform plan`, 
que confirma que a única barreira restante são credenciais reais da AWS — não 
uma falha no código. O projeto está pronto para ser aplicado (`terraform apply`) 
assim que uma conta AWS estiver disponível.

## Tecnologias usadas

- **Terraform** (Infrastructure as Code)
- **AWS Provider** (hashicorp/aws)

## Como testar

```bash
git clone https://github.com/nicolasalexferrari/aws-secure-infra-terraform.git
cd aws-secure-infra-terraform
terraform init
terraform validate
```

(Opcional, para ver o comportamento esperado sem credenciais reais: `terraform plan`)

## O que eu aprendi

Este projeto me apresentou à diferença entre programação imperativa e declarativa. 
No projeto anterior (Python), eu precisava descrever passo a passo o que o código 
deveria fazer. Aqui, com Terraform, eu só declaro o resultado final desejado, e a 
ferramenta calcula sozinha como chegar lá. Também tive meu primeiro contato prático 
com criptografia de dados em nuvem, um tema que despertou bastante meu interesse 
dentro de segurança em nuvem.

Este é meu segundo projeto voltado a segurança em nuvem, feito enquanto estudo 
Engenharia de Software (Cruzeiro do Sul) e Cibersegurança (FIAP e Google, via CIEE).