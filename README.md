☁️ Implantação de Servidor Web Seguro na AWS (EC2 + S3 + IAM)

Projeto prático desenvolvido durante os estudos para a certificação AWS Certified Cloud Practitioner (CLF-C02). 
Cursando também de Análise e Desenvolvimento de Sistemas (ADS).

🎯 Objetivo

Provisionar e configurar uma infraestrutura básica na nuvem da Amazon Web Services (AWS), implementando um servidor web Apache em uma instância Linux e aplicando o princípio do menor privilégio para comunicação segura com o Amazon S3 via IAM Roles, sem chaves de acesso gravadas na máquina.

🛠️ Tecnologias e Serviços Utilizados
Cloud Provider: Amazon Web Services (AWS)
Computação: Amazon EC2 (t3.micro / Amazon Linux 2023)
Armazenamento: Amazon EBS (Volume raiz de 8 GB) e Amazon S3
Segurança: AWS IAM (Instance Profile / Roles) e Security Groups (Stateful Firewall)
Redes: Amazon VPC, Subnet pública e Elastic IPv4
Servidor Web: Apache HTTP Server (httpd)
Terminal & Acesso: SSH via PuTTY com chave criptográfica assimétrica (.ppk)
📐 Arquitetura da Solução
text
[Usuário / Navegador]
        │ (Porta 80 - HTTP)
        ▼
[Security Group (Firewall)]
        │
        ▼
[Instância EC2 (Amazon Linux 2023 + Apache)] ──(IAM Role)──► [Bucket Amazon S3]
🔒 Boas Práticas e Conceitos de Nuvem Aplicados
Princípio do Menor Privilégio (Least Privilege):
Nenhuma credencial fixa (AWS_ACCESS_KEY_ID / AWS_SECRET_ACCESS_KEY) foi gravada no servidor. O acesso ao bucket S3 foi concedido através de uma IAM Role (Instance Profile), utilizando credenciais temporárias rotacionadas automaticamente pela AWS.
Firewall Mínimo Necessário (Security Group):
Configuração de regras restritas: liberação de tráfego web público apenas na porta 80 (HTTP) e acesso administrativo restrito na porta 22 (SSH).
Resiliência e Armazenamento Persistente:
Utilização de volume de bloco Amazon EBS para persistência do sistema operacional e arquivos do servidor.
Higiene de Custos (FinOps):
Uso de instâncias elegíveis aos créditos de estudante e planejamento do ciclo de vida dos recursos (Terminate após a validação).
📸 Evidências do Projeto
1. Servidor Web Apache Rodando no Navegador (IP Público)



<img width="981" height="569" alt="01-pagina-web-apache" src="https://github.com/user-attachments/assets/b76252b2-1d8d-4ab9-8297-28c44b082542" />



2. Acesso ao Amazon S3 via Terminal PuTTY (Autenticação via IAM Role)



<img width="715" height="429" alt="02-terminal-putty-aws-cli-s3" src="https://github.com/user-attachments/assets/c3a69c41-910d-4011-8fc3-ea3302f8455d" />



3. Painel de Controle EC2 no Console AWS (Instância Executando)



<img width="1278" height="592" alt="03-instancia-ec2-executando" src="https://github.com/user-attachments/assets/4f8a0774-4b8b-4104-8ec6-0ed5a0aeef0a" />



4. Detalhes Técnicos da Instância (AMI e Par de Chaves)



<img width="1217" height="506" alt="04-detalhes-tecnicos-ami" src="https://github.com/user-attachments/assets/de21db20-92da-4f49-b11e-03f168143b25" />



5. Configuração do Firewall (Security Group)



<img width="1296" height="525" alt="05-security-group-firewall" src="https://github.com/user-attachments/assets/c383d79b-84b7-42e6-8ac5-f6a17af2e3a7" />



6. Armazenamento em Bloco (Amazon EBS)



<img width="1294" height="313" alt="06-volume-armazenamento-ebs" src="https://github.com/user-attachments/assets/899aa1cc-2c47-4ecf-9f73-e7ee521eea6b" />


