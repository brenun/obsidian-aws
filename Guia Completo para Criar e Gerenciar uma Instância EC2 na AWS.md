
1. No canto superior direito destas instruções, clique em **Start Lab** (Iniciar Laboratório)
    
    - Dica: Se aparecer um erro "Access Denied", feche a mensagem e clique em **Start Lab** novamente
        
2. Observe o círculo de status no canto superior esquerdo:
    
    - 🔴 Vermelho: Laboratório não iniciado
        
    - 🟡 Amarelo: Laboratório iniciando
        
    - 🟢 Verde: Laboratório pronto
        
3. Quando estiver verde, clique no círculo para abrir o Console AWS em nova aba
    
    - Se não abrir, verifique se seu navegador não está bloqueando pop-ups
        
4. Organize as abas para ver ambas simultaneamente
    
    - Importante: Não altere a Região do laboratório
        

## Tarefa 1: Iniciando sua Instância EC2

### Passo 1: Nomeando sua instância

1. No console AWS, vá em **Serviços** > **EC2**
    
2. No painel esquerdo, clique em **EC2 Dashboard**
    
3. Clique em **Launch Instance** > **Launch Instance** novamente
    
4. No campo **Name**, digite "Web Server"
    

### Passo 2: Escolhendo uma AMI

- Mantenha selecionada a AMI padrão: **Amazon Linux 2 AMI**
    

### Passo 3: Escolhendo tipo de instância

- Selecione **t3.micro** (2 vCPUs, 1 GiB de memória)
    

### Passo 4: Configurando par de chaves

- Selecione **Proceed without a key pair** (Não recomendado)
    

### Passo 5: Configurando rede

1. Clique em **Edit** em Network Settings
    
2. Selecione **Lab VPC**
    
3. Configure o Security Group:
    
    - Nome: "Web Server security group"
        
    - Descrição: "Security group for my web server"
        
4. Remova a regra SSH existente (para maior segurança)
    

### Passo 6: Armazenamento

- Mantenha o volume padrão de 8 GiB
    

### Passo 7: Detalhes avançados

1. Expanda **Advanced details**
    
2. Em **Termination protection**, selecione **Enable**
    
3. Em **User data**, cole o script:

`#!/bin/bash`
`yum -y install httpd`
`systemctl enable httpd`
`systemctl start httpd`
`echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html`

### Passo 8: Lançando a instância

1. Clique em **Launch instance**
    
2. Clique em **View all instances**
    
3. Aguarde até que:
    
    - Instance State: **Running**
        
    - Status Checks: **2/2 checks passed**
        

## Tarefa 2: Monitorando sua Instância

1. Selecione sua instância e vá para a aba **Status checks**
    
    - Verifique se ambas as verificações passaram
        
2. Na aba **Monitoring**, veja as métricas do CloudWatch
    
    - Clique em qualquer gráfico para ampliar
        
3. Em **Actions** > **Monitor and troubleshoot** > **Get Instance Screenshot**
    
    - Isso mostra como estaria o console da instância
        
    - Clique em **Cancel** para fechar
        

## Tarefa 3: Acessando o Servidor Web

1. Na aba **Details**, copie o **Public IPv4 address**
    
2. Cole em uma nova aba do navegador - não funcionará ainda
    
3. Volte ao console EC2 e vá para **Security Groups**
    
4. Selecione seu security group e edite as **Inbound rules**
    
5. Adicione uma nova regra:
    
    - Type: **HTTP**
        
    - Source: **Anywhere-IPv4**
        
6. Salve e atualize a página no navegador
    
    - Agora você verá "Hello From Your Web Server!"
        

## Tarefa 4: Redimensionando a Instância

### Parando a instância:

1. Vá para **Instances**
    
2. Selecione sua instância
    
3. Em **Instance state**, clique em **Stop instance**
    
4. Confirme e aguarde até **stopped**
    

### Alterando tipo de instância:

1. Em **Actions** > **Instance Settings** > **Change Instance Type**
    
2. Mude para **t3.small**
    
3. Clique em **Apply**
    

### Redimensionando volume EBS:

1. Vá para **Volumes**
    
2. Selecione o volume associado
    
3. Em **Actions**, clique em **Modify Volume**
    
4. Mude para **10 GiB**
    
5. Confirme com **Modify**
    

### Iniciando a instância:

1. Volte para **Instances**
    
2. Em **Instance state**, clique em **Start instance**
    

## Tarefa 5: Testando Proteção contra Término

1. Tente terminar a instância:
    
    - **Actions** > **Instance State** > **Terminate instance**
        
    - Você receberá uma mensagem de erro
        
2. Para desativar a proteção:
    
    - **Actions** > **Instance Settings** > **Change termination protection**
        
    - Desmarque **Enable** e salve
        
3. Agora você pode terminar a instância:
    
    - **Actions** > **Instance State** > **Terminate instance**
        
    - Confirme com **Terminate**

