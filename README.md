# Projeto Compass EC2 Linux NFS e APACHE

1. Requisitos AWS

1.1. Criar Instância EC2

Passos:

No console AWS, vá para EC2 > Executar Instância.

Escolha o Amazon Linux 2 como sistema operacional.

Em Tipo de Instância, selecione a família t3.small.

Em Armazenamento, defina o tamanho do SSD como 16 GB.

Associe a chave pública gerada anteriormente e Lance a Instância.

1.2. Gerar e Associar Elastic IP

No console AWS, acesse EC2 > Ips Elásticos.

Selecione Alocar Endereço de IP Elástico.

Clique em Alocar.

Após gerar o Elastic IP, clique em Ações > Associar Endereço de IP Elástico e associe-o à instância EC2 recém-criada.

1.3. Configurar Regras de Segurança para Acesso

No Security Groups da instância EC2, edite as regras de entrada.

Adicione as seguintes regras:

Porta 22/TCP para SSH.
Porta 80/TCP para HTTP.
Porta 443/TCP para HTTPS.
Porta 111/TCP e UDP 
2049/TCP e UDP para NFS.

2. Montando o NFS e Apache

2.1. Instale os pacotes necessários para o NFS:

sudo yum install -y nfs-utils

Crie o diretório para montar o NFS:

Edite o arquivo /etc/fstab para montar o NFS automaticamente:

2.2. Criar Diretório Pessoal no NFS

Crie um diretório com o seu nome dentro do NFS montado:

2.3. Instalar e Configurar o Apache

Instale o Apache:

sudo yum install -y httpd

Inicie o Apache e habilite-o para iniciar no boot:

sudo systemctl start httpd
sudo systemctl enable httpd

Verifique se o serviço está rodando:

sudo systemctl status httpd

2.4. Crie um script para validar o status do Apache

2.5. Agende uma Execução Automática (Cron)

Edite a crontab para que o script seja executado a cada 5 minutos:
