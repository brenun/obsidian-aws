### **Serviços de armazenamentos:**
**Amazon s3** é um serviço de armazenamento onde guardamos nossos arquivos.

**EBS:** Conecta com EC2 apenas 

**A categoria S3 Glacier** é uma classe de armazenamento de nuvem, durável de custo baixo para arquivamento de dados e backup de longo prazo. foi projetado para oferecer mais de 11 noves(99,99999999999%) de durabilidade e oferece recursos abrangentes de segurança e conformidade para atender exigências rigorosas.

### **Serviço de computação:**

**Amazon s2**

**Amazon EC2 Auto Scaling**: Consegue fazer um escalonamento vertical tanto para cima, quanto para baixo, pois ele entrega uma escalabilidade. 

> [!Nota!] C2 e EC2 trabalham em conjunto 

**AWS Elastic Beanstalk**: ele não permite escoabilidade, mas permite dimensionamento de aplicativos e serviços web.

**AWS Lambda:** permite executar código sem provisionamento ou gerenciamento de servidores, permite uso gratuito. (==Não cria EC2==)

### **Serviço de Contêiner:**

**ECS**: Presta serviço de container para AWS, roda dentro da maquina, mas não esta ligado ao sistema operacional. (Cria containers)

**Amazon Elastic Container Registry:** Registra a imagem gerada pelo container ECS.

**EKS (Kubernetes):** Faz gerenciamento dos containers (apenas serviço pago!) 

**Fargate**: Permite executar containers sem gerenciar servidores ou clusters. Sem automatização, diminui ou aumenta containers.

### **Serviço Banco de Dados:**

**Amazon RDS:** Principal serviço de dados utilizado. Facilita a criação, operação e dimensionamento de um banco de dados relacional na nuvem. Oferece capacidade redimensionável enquanto automatiza tarefas administrativas demoradas, como provisionamento de hardware, configuração de banco de dados, aplicação de patches e backups. 

**Aurora**: Compatível com MySQL e PostgreSQL apenas, alem de ser cinco vezes mais rápido que o RDS.

> [!NOTE] RDS e Aurora, utilizados pela AWS e são bancos de dados relacionais.

**Amazon Redshift:** ==Para grande volumes de dados==. também é possível fazer consultas diretamente contra exabytes de dados armazenamos no amazon S3. Oferece serviço rápido em qualquer escala.

**Dynamo BD:** É possível montar tabelas diretamente nele. Banco de dados de documentos e chave valor que oferece desempenho de milissegundos de um digito em qualquer escala, com segurança, backup e restauração incorporados, bem como cache na memória. 

### **Serviço de Redes e entrega de Conteúdo**

**Amazon VPC:** permite provisionar seções logicamente isoladas da AWS Cloud.

**Elastic Load Balancing:** Distribui automaticamente o tráfego de entrada de aplicações em diversos destinos, como instancias EC2 da Amazon, contêineres, endereços IP e funções Lambda.

**CloudFront:** É um serviço rápido de rede de entrega de conteúdo (CDN) que entrega com segurança dados, vídeos, aplicativos e interfaces de programação de aplicativo (APIs) a clientes em todo o mundo, com baixa latência e alta velocidade de transferência. (como deixasse o arquivo mais próximo do cliente).

**AWS Transit Gateway:** é um serviço que permite aos clientes conectar nuvens virtuais privadas (VPCs) e redes no local a um único gateway.

**Amazon route 53:** É um serviço da Amazon para traduzir nomes de sites (como www.example.com) em endereços IP que os computadores entendem, ajudando os usuários a acessar os aplicativos na internet de forma confiável. ==Porém, ele também pode fazer o processo inverso, chamado de **DNS reverso**.==

**AWS Direct Connect:** Oferece uma conexão privada direta entre seu escritório ou datacenter e a AWS. Isso pode melhorar a velocidade e reduzir custos de rede.

**AWS VPN:** Cria um túnel seguro e privado entre a sua rede ou dispositivo e a rede global da AWS.

### **Serviços de Segurança, Identidade e Conformidade de AWS**

**AWS IAM:** Gerencia o acesso seguro aos serviços e recursos da AWS, permitindo criar usuários e grupos e definir permissões para controlar o acesso. - ==Usuário==

**AWS Organizations:** Ajuda a restringir quais serviços e ações podem ser utilizados nas contas da AWS. - ==Contas==

**Amazon Cognito:** facilita o controle de acesso, inscrição e login de usuários em aplicativos web e móveis; - ==Autenticação==

**AWS Artifact:** Fornece acesso sob demanda a relatórios de segurança e conformidade da AWS. - ==Baixar Certificados== 

**AWS KMS:** Permite criar e gerenciar chaves para usar criptografia em vários serviços da AWS. - ==Gerenciamento de Chaves== 

**AWS Shield:** Protege contra ataques de negação de serviço (DDoS) em aplicativos executados na AWS.  - ==Proteger Arquivos de ataques DDoS==

### Serviços de gerenciamento de Custos da AWS

**AWS Cost and Usage Report:** Oferece dados completos sobre custos e uso da AWS, incluindo informações detalhadas sobre serviços e preços.

**AWS Budgest:** Permite criar orçamentos personalizados e envia alertas quando os custos ou o uso ultrapassam (ou têm previsão de ultrapassar) o valor definido.

**AWS Cost Explorer:** Apresenta uma interface fácil para visualizar, entender e gerenciar os custos e o uso da AWS ao longo do tempo.

### Serviço de Gerenciamento e governança

**AWS Management Console:** Interface web para acessar e gerenciar sua conta AWS

**AWS Config:** Rastreia e monitora inventário e mudanças de recursos na AWS.

**Amazon CloudWatch:** Monitora recursos e aplicativos da AWS

**AWS Auto Scaling:** Ajusta recursos automaticamente conforme a demanda

**AWS CLI (Comand Line Interface):** Ferramenta para gerenciar serviços AWS via linha de comando.

**AWS Trusted Advisor:** Ajuda a melhorar desempenho e segurnaça

**AWS Well-Architected Tool:** Auxilia na análise e melhoria de cargas de trabalho

**AWS CloudTrall:** Registra a atividade de usuários e APIs na AWS