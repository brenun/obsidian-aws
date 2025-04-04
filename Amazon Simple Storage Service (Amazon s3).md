
- Os dados são armazenados como objetos em buckets e não possuem limite de armazenamento!
- Um único objeto pode ter até 5 TB
- Projetado para 11 noves (99,999999999%) de durabilidade
- Os uploads precisam ser particionados com no max 5 gb por objeto
- Pode armazenar virtualmente quantos objetos quiser 
- Por padrão os dados são privados, e você tem a opção de criptografá-los
- Os dados são armazenados de forma redundante
- É possível recuperar dados a qualquer momento e em qualquer lugar pela internet
- Os nomes de buckets devem ser exclusivos entre todos os nomes de buckets existentes no Amazon S3.

### Classes de armazenamento do Amazon S3

- Amazon S3 Standard
- Amazon S3 Inteligent-Tiering
- Amazon S3 Standard-Infrequent Access (Amazon S3 Standard-IA)
- Amazon S3 One Zone-infrequent Access (Amazon S3 One Zone-IA)
- Amazon Simple Storage Service Glacier 
- Amazon S3 Glacier Deep Archive

1. **Amazon S3 Standard**
    
    - Alta durabilidade, disponibilidade e desempenho.
        
    - Ideal para dados acessados frequentemente.
        
    - Usado em aplicativos de nuvem, sites, análise de big data, entre outros.
        
2. **Amazon S3 Intelligent-Tiering**
    
    - Otimiza custos movendo dados automaticamente para o nível mais econômico baseado no padrão de acesso.
        
    - Sem impacto no desempenho ou taxas extras de recuperação.
        
    - Bom para dados de longa duração com padrões de acesso imprevisíveis.
        
3. **Amazon S3 Standard-Infrequent Access (S3 Standard-IA)**
    
    - Para dados menos acessados, mas que precisam de recuperação rápida.
        
    - Combina baixo custo e alto desempenho.
        
    - Adequado para backups e recuperação de desastres.
        
4. **Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA)**
    
    - Dados menos acessados armazenados em uma única zona de disponibilidade.
        
    - Custo mais baixo que o S3 Standard-IA.
        
    - Útil para backups secundários ou dados fáceis de recriar.
        
5. **Amazon S3 Glacier**
    
    - Armazenamento seguro e barato para arquivamento de longo prazo.
        
    - Oferece 3 opções de recuperação, de minutos a horas.
        
    - Ideal para transferir dados inativos.
        
6. **Amazon S3 Glacier Deep Archive**
    
    - A opção mais barata para retenção de longo prazo (dados acessados 1-2 vezes por ano).
        
    - Alvo de conformidade regulatória e substituição de fitas magnéticas.
        
    - Recuperação em até 12 horas.


>   É possível acessar o Amazon S3 por meio do console de gerenciamento da AWS, da AWS Command Line Interface (AWS CLI) ou dos Kits de Desenvolvimento de Software (SDKs) da AWS
> 
> Além disso, é possível acessar os dados no bucket diretamente, usando endpoints baseados em REST, compatíveis com o acesso por Hypertext Transfer Protocol (HTTP) ou Secure (HTTPS). 


![[Pasted image 20250402192939.png]]

%% **O S3 foi projetado para dimensionamento ininterrupto** %%

#### **Casos de uso comuns do Amazon S3**
- Armazenamento de ativos de aplicativos 
- Hospedagem na web de sites estáticos
- Backup e recuperação de desastres (DR)
- Área de preparação para big data
- E muito mais...

#### Modelo de preço do Amazon S3

**Pague somente pelo que usa:**
- GBs por mês
- Transferencia para FORA, para outras Regiões
- Solicitações PUT, COPY, LIST e GET

**Você NÃO precisa pagar por:**
- Transferir PARA o Amazon S3
- Transferência para FORA do Amazon S3 para o Amazon CloudFront ou Amazon EC2 na mesma Região.


#### Estimativa de custo do Amazon S3

1. **Tipo de classe de armazenamento**
    
    - **Amazon S3 Standard**: Alta durabilidade (11 noves) e disponibilidade (4 noves).
        
    - **Amazon S3 Standard-Infrequent Access (S-IA)**: Menor redundância e custo, com mesma durabilidade (11 noves) e menor disponibilidade (3 noves).
        
2. **Quantidade de armazenamento**
    
    - Custo baseado no número e no tamanho dos objetos armazenados.
        
    - O tipo de armazenamento também influencia os gastos.
        
3. **Solicitações (operações)**
    
    - **GET**: Recupera objetos; requer acesso de leitura.
        
    - **PUT**: Adiciona objetos a um bucket; requer permissão de gravação.
        
    - **COPY**: Duplica objetos existentes, combinando GET e PUT.
        
    - Cada tipo de solicitação possui uma cobrança específica.
        
4. **Transferência de dados**
    
    - Transferências dentro da mesma Região são gratuitas.
        
    - Transferências para fora da Região geram cobranças.
