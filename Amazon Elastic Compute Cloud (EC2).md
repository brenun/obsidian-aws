
**Serviços principais da AWS**
- Base para construir soluções 

**Amazon Elastic Compute Cloud (Amazon EC2)**
- Serviço computacional princiapal da AWS
- Atende desde aplicativos móveis simples até clusters massivos para tarefas complexas, como sequenciamento genético;

**Catálogo de serviços computacionais**
- Abrange desde serviços simples de aplicativos até servidores virtuais flexíveis.
- Inclui também computação sem servidor.


![[Pasted image 20250402203259.png]]

![[Pasted image 20250402203338.png]]

- **Servidores no local**
    
    - Altos custos de aquisição de hardware e manutenção de data centers.
        
    - Capacidade ociosa em servidores, causando desperdício.
        
    - Necessidade de provisionamento para picos de tráfego, o que aumenta despesas.
        
- **Amazon EC2**
    
    - Oferece máquinas virtuais na nuvem com capacidade segura e redimensionável.
        
    - Substitui servidores locais para múltiplas aplicações.
        
    - Reduz custos e aumenta eficiência.
        
- **Usos comuns do Amazon EC2**
    
    - Servidores: aplicativos, web, banco de dados, jogos, e-mail, mídia, catálogos, arquivos, computação e proxy.


### Passo a passo para Executar uma Instância do EC2

![[Pasted image 20250402203613.png]]

![[Pasted image 20250402203626.png]]

![[Pasted image 20250402203651.png]]
![[Pasted image 20250402203707.png]]
![[Pasted image 20250402203734.png]]

![[Pasted image 20250402203750.png]]

- **Variabilidade dos tipos de instância**
    
    - Diferem em CPU, núcleos, armazenamento, memória e desempenho de rede.
        
- **Instâncias T3**
    
    - Uso geral com capacidade de intermitência acima da linha de base.
        
    - Casos de uso: sites, aplicativos web, ambientes de desenvolvimento, microsserviços, testes e preparação.
        
- **Instâncias C5**
    
    - Otimizadas para cargas de trabalho intensivas em computação.
        
    - Casos de uso: modelagem científica, processamento em lote, anúncios, jogos multijogador e codificação de vídeo.
        
- **Instâncias R5**
    
    - Focadas em aplicativos com uso intensivo de memória.
        
    - Casos de uso: bancos de dados de alto desempenho, análise de dados, caches distribuídos e processamento de big data.


![[Pasted image 20250402204020.png]]
- **Escolha da AMI e tipo de instância**
    
    - Selecione a AMI e o tipo de instância antes de configurar a rede.
        
- **Escolha da Região**
    
    - Certifique-se de estar na Região correta no console do Amazon EC2 antes de iniciar a instância.
        
- **Endereçamento IP em VPCs**
    
    - **VPC padrão**: A AWS atribui um endereço IP público automaticamente.
        
    - **VPC não padrão**: Atribuição de IP público depende do atributo da sub-rede.
        
- **Controle do IP público**
    
    - Modifique o atributo de endereçamento IP público da sub-rede.
        
    - Habilite ou desabilite o recurso de IP público durante a inicialização.


![[Pasted image 20250402204201.png]]
- **Funções do IAM em instâncias do EC2**
    
    - Permitem chamadas seguras de API para outros serviços da AWS.
        
    - Substituem a necessidade de armazenar credenciais da AWS diretamente na instância (prática insegura).
        
- **Perfil de instância**
    
    - Contêiner para uma função do IAM.
        
    - Criado automaticamente pelo console da AWS ao associar uma função ao EC2.
        
- **Configuração de funções do IAM**
    
    - Pode ser feita ao iniciar a instância ou em uma instância já em execução.
        
    - Define permissões para contas ou serviços que podem assumir a função.
        
    - Especifica ações e recursos da API que o aplicativo pode usar.
        
- **Propagação de alterações**
    
    - Alterações em uma função são aplicadas automaticamente a todas as instâncias associadas.


![[Pasted image 20250402204324.png]]

- **Automatização com dados do usuário**
    
    - Permite automatizar instalações e configurações ao iniciar a instância.
        
    - Exemplos: aplicar patches, atualizar sistema operacional, instalar software e chaves de licença.
        
- **Scripts de dados do usuário**
    
    - **Linux**: Scripts em Bash podem usar ferramentas como YUM para atualizar pacotes e Wget para baixar arquivos.
        
    - **Windows**: Scripts devem ser compatíveis com o prompt de comando ou PowerShell.
        
- **Execução dos scripts**
    
    - **Linux**: Executados pelo serviço cloud-init.
        
    - **Windows**: Executados pelo EC2Config ou EC2Launch.
        
    - Por padrão, os scripts são executados apenas na primeira inicialização da instância.
        
- **Execução repetida**
    
    - Para executar o script em todas as inicializações, crie um arquivo MIME de várias partes (não é comum).


![[Pasted image 20250402204431.png]]

#### Opções de armazenamento do Amazon EC2

![[Pasted image 20250402204526.png]]

- **Amazon Elastic Block Store (Amazon EBS)**
    
    - Armazenamento em bloco durável e de alto desempenho para uso com o Amazon EC2.
        
    - Ideal para cargas de trabalho intensivas em transações e taxas de transferência.
        
    - Permite ajustar tipos de volume, desempenho e tamanho sem interrupções.
        
- **Armazenamento de Instâncias do Amazon EC2**
    
    - Armazenamento temporário em nível de bloco, anexado fisicamente ao host.
        
    - Útil para dados temporários, como buffers, caches e dados replicados.
        
    - Dados são excluídos se a instância for interrompida.
        
- **Amazon Elastic File System (Amazon EFS)**
    
    - Sistema de arquivos NFS gerenciado, dimensionável e elástico.
        
    - Ajusta automaticamente a capacidade conforme os arquivos são adicionados ou removidos.
        
    - Ideal para aplicações que precisam de armazenamento escalável.
        
- **Amazon Simple Storage Service (Amazon S3)**
    
    - Armazenamento de objetos com alta escalabilidade, segurança e desempenho.
        
    - Usado para backup, restauração, arquivos, IoT, big data e mais.


![[Pasted image 20250402204630.png]]
- **Exemplo Instância 1**
    
    - **Volume raiz**: Armazenado no Amazon EBS (20 GB).
        
    - **Volumes adicionais**: Um volume EBS (500 GB) e um volume de armazenamento de instâncias (temporário).
        
    - **Persistência de dados**: Dados nos volumes EBS permanecem intactos se a instância for reiniciada. Dados no volume temporário são perdidos permanentemente.
        
    - **Uso do armazenamento de instâncias**: Ideal para dados temporários, como buffers e caches.
        
- **Exemplo Instância 2**
    
    - **Volume raiz**: Armazenamento de instâncias (temporário).
        
    - **Limitações**: Não pode ser parada via API, apenas encerrada.
        
    - **Perda de dados**: Dados no volume raiz são perdidos se a instância for encerrada.
        
    - **Recomendação**: Não use armazenamento de instâncias para dados valiosos. Prefira Amazon EBS, Amazon EFS ou Amazon S3 para maior durabilidade.


![[Pasted image 20250402204730.png]]

![[Pasted image 20250402204750.png]]

![[Pasted image 20250402204807.png]]


![[Pasted image 20250402204946.png]]

- **Painel Description (Descrição)**
    
    - Exibe informações detalhadas sobre a instância.
        
    - Inclui endereço IP, endereço DNS, tipo de instância, ID da instância, ID da AMI, ID da VPC, ID da sub-rede e outros detalhes.
        
- **Hiperlinks**
    
    - Muitos dos detalhes possuem hiperlinks.
        
    - Permitem acessar informações adicionais sobre os recursos da instância.


![[Pasted image 20250402205046.png]]

- **Execução programática**
    
    - Pode ser feita usando a AWS CLI ou os SDKs da AWS.
        
- **Comando AWS CLI**
    
    - **aws**: Invoca o utilitário de linha de comando.
        
    - **ec2**: Especifica o serviço EC2.
        
    - **run-instances**: Subcomando para iniciar instâncias.
        
- **Parâmetros do comando**
    
    - **image-id**: ID exclusiva da AMI.
        
    - **count**: Número de instâncias a criar.
        
    - **instance-type**: Tipo de instância (ex.: c3.large).
        
    - **key-name**: Nome do par de chaves existente.
        
    - **security-groups**: Nome do grupo de segurança existente.
        
    - **region**: Região da AWS onde a AMI está localizada.
        
- **Requisitos para sucesso**
    
    - Comando bem formado.
        
    - Recursos necessários existentes.
        
    - Permissões suficientes.
        
    - Capacidade disponível na conta AWS.
        
- **Resposta da API**
    
    - Retorna a ID da instância e outros dados relevantes para uso em solicitações futuras.


![[Pasted image 20250402205158.png]]
- **Pendente**
    
    - Estado inicial ao executar ou reiniciar uma instância.
        
    - A instância é inicializada e implantada no hardware especificado.
        
- **Em execução**
    
    - A instância está pronta e conectável pela Internet.
        
- **Reinicialização**
    
    - Recomenda-se reiniciar pelo console da AWS, CLI ou SDKs.
        
    - Mantém o mesmo host físico, DNS público e IP público.
        
    - Dados em volumes de armazenamento de instâncias são preservados.
        
- **Desligando**
    
    - Estado intermediário antes de ser encerrada.
        
- **Encerrada**
    
    - Instância não pode ser conectada ou recuperada.
        
    - Permanece visível no console por um tempo antes de ser excluída.
        
- **Interrupção**
    
    - Instâncias baseadas em EBS podem ser interrompidas.
        
    - Entram no estado de interrupção antes de serem totalmente interrompidas.
        
- **Interrompida**
    
    - Não gera custos como uma instância em execução.
        
    - Ao ser reiniciada, retorna ao estado pendente em um novo host.


#### Modelos de preço do Amazon EC2

- **Faturamento por segundo**
    
    - Disponível para instâncias sob demanda, reservadas e spot que executam Amazon Linux ou Ubuntu.
        
- **Instâncias sob demanda**
    
    - Menor custo inicial e maior flexibilidade.
        
    - Sem compromissos de longo prazo.
        
    - Ideal para cargas de trabalho de curto prazo, picos ou imprevisíveis.
        
- **Hosts dedicados**
    
    - Servidores físicos exclusivos para o cliente.
        
    - Permitem usar licenças de software existentes (ex.: Microsoft Windows).
        
- **Instâncias dedicadas**
    
    - Executadas em hardware dedicado a um único cliente.
        
    - Isoladas fisicamente de outras contas da AWS.
        
- **Instâncias reservadas**
    
    - Capacidade reservada por 1 ou 3 anos com custos reduzidos.
        
    - Ótimas para uso consistente e pesado.
        
- **Instâncias reservadas programadas**
    
    - Reservas de capacidade recorrentes (diárias, semanais ou mensais).
        
    - Pagamento pelo período programado, mesmo sem uso.
        
- **Instâncias spot**
    
    - Permitem sugerir preços para instâncias não utilizadas.
        
    - Custos reduzidos, com preço por hora variável conforme oferta e demanda.


#### Modelos de preço do Amazon EC2: Benefícios

- **Instâncias sob demanda**
    
    - Maior flexibilidade.
        
    - Sem contratos de longo prazo.
        
    - Taxas baixas, ideal para cargas de trabalho imprevisíveis ou de curto prazo.
        
- **Instâncias spot**
    
    - Oferecem grande escala a um custo significativamente menor.
        
- **Instâncias reservadas**
    
    - Ótimas para necessidades de computação previsíveis ou estáveis.
        
    - Econômicas para uso prolongado (meses ou anos).
        
- **Hosts dedicados**
    
    - Servidores físicos exclusivos.
        
    - Atendem a restrições de licenciamento ou requisitos de conformidade.


#### Modelos de preço do Amazon EC2: Casos de uso

- **Instâncias sob demanda**
    
    - Ideais para cargas de trabalho com picos, imprevisíveis ou de curto prazo.
        
    - Úteis para desenvolvimento e testes de aplicativos.
        
- **Instâncias spot**
    
    - Recomendadas para aplicativos tolerantes a falhas que podem lidar com interrupções (aviso de 2 minutos).
        
    - Casos de uso: servidores web, back-ends de API, processamento de big data e cargas que salvam dados em armazenamento persistente (ex.: Amazon S3).
        
- **Instâncias reservadas**
    
    - Ótimas para cargas de trabalho de longo prazo e uso previsível.
        
    - Econômicas para servidores executados consistentemente por meses ou anos.
        
- **Hosts dedicados**
    
    - Adequados para licenças de software específicas (por soquete, núcleo ou VM).
        
    - Atendem a requisitos de conformidade corporativa e regulamentar.