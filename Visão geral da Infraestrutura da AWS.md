![[Pasted image 20250328205029.png]]

A infraestrutura global da AWS pode ser dividida em três elementos: 
1. Regiões
2. Zonas de Disponibilidade
3. Pontos de presença

- Uma **Região da AWS** é uma **Área geográfica** 
- Cada **Região** é composta por duas ou mais **Zonas de Disponibilidades**
- Podemos habilitar e controlar a replicação de dados entre regiões.
- Atualmente temos 36 regiões

## **Regiões da AWS**

### Conceitos Principais 

1. **O que é uma Região AWS?**
- Localização geográfica física a AWS possui múltiplas Zonas de Disponibilidade (AZs)
- Isoladas entre si para garantir tolerância a falhas e estabilidade.

2. **Zonas de Disponibilidades (AZs)**
- Cada Região tem pelo menos 2 AZs

3. **Replicação de Dados**
- **Não é automática entre Regiões** - o usuário deve gerenciar a replicação se necessário.
- **Dados nunca saem da Região escolhida**, a menos que você os mova.

4. **Escolha da Região**
Baseada em:
- Conformidade regulatória (LGPD)
- Latência de rede (proximidade dos usuários/clientes)

5. **Vantagens de Multi-Regiões**
- **Redução de latência:** implante aplicações perto dos usuários
- **Agilidade e baixo custo:** implante em minutos com alguns cliques.

6. **Regiões com Acesso Restrito**
- Exemplo: **AWS GovCloud (EUA**) para cargas de trabalho governamentais sensíveis. 

#### **Destaques para Estudo**

✔ **Regiões ≠ Zonas de Disponibilidade** (Regiões contêm AZs).  
✔ **Dados não replicam automaticamente** entre Regiões – responsabilidade do usuário.  
✔ **Conformidade e latência** são fatores críticos na escolha da Região.  
✔ **Multi-Regiões melhoram performance** para usuários distribuídos.

**Exemplo Prático:**

- Clientes na Virgínia (EUA)? Implante na **Região Leste dos EUA** para menor latência.

#### Seleção de uma Região
1. Governança de dados, requisitos legais
2. Proximidade com os clientes (latência)
3. Serviços disponíveis na Região
4. Custos (variam de acordo com a região)

#### Pontos de presença
Composta por 205 locais de borda (ou ponto de presença) e 11 caches de borda regionais

> [!Empresas de streaming utilizam esse modelo para diminuir a latência de seus usuários]
> Juntamente com o ==Amazon CloudFront== uma rede de entrega de conteúdo (CDN) distribui aos usuários com a latência reduzida. 
> [^1]
> [^2]

[^1]: Então uma empresa pode abrir o seu servidor em outro pais para reduzir custos mas criar um ponto de presença em outra região para poder diminuir a latênci

[^2]: Existem as Local Zones, que são locais próximos a regiões para que seja possível diminuir a latência daquele local distante da região. 


