# Análise de Padrões de Apostas e Identificação de Jogadores de Risco

Projeto de análise de dados desenvolvido como case técnico para a H2 Poker, com foco na identificação de padrões de apostas, movimentações financeiras atípicas e possíveis comportamentos de risco em uma plataforma de jogos online.

> **Observação:** os dados originais não estão incluídos neste repositório por conterem informações operacionais e potencialmente sensíveis. O objetivo deste repositório é apresentar a metodologia, o raciocínio analítico, os indicadores criados e os principais aprendizados do projeto.

## Visão geral

O projeto analisa o comportamento de jogadores a partir de três bases principais:

- `casino_activity.csv`: histórico de apostas dos jogadores, incluindo jogo, tipo de jogo, valor apostado, quantidade de apostas e valor ganho.
- `client.csv`: informações cadastrais e de origem dos jogadores, como idade, gênero e canais de entrada.
- `financial_activity.csv`: movimentações financeiras dos jogadores, incluindo depósitos e solicitações de saque.

A partir dessas bases, foram realizadas análises exploratórias, criação de métricas de comportamento e definição de regras para sinalização de possíveis jogadores de risco.

## Objetivos do projeto

- Investigar padrões de apostas e ganhos dos jogadores.
- Identificar jogadores com taxa de retorno muito acima do comportamento esperado.
- Avaliar concentração de apostas em jogos com alta taxa de retorno.
- Detectar movimentações financeiras suspeitas, como saques elevados em relação aos depósitos.
- Criar regras estatísticas simples e interpretáveis para apoiar o monitoramento operacional.
- Transformar dados brutos em recomendações acionáveis para segurança, produto e operação.

## Perguntas norteadoras

- Quais jogadores apresentam comportamentos atípicos de apostas e ganhos?
- Existem jogos com concentração de apostas e alta taxa de retorno?
- Quais jogadores realizam movimentações financeiras suspeitas?
- Como criar critérios objetivos para monitoramento e mitigação de riscos?
- Como reduzir falsos positivos sem deixar de identificar padrões relevantes?

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab
- Jupyter Notebook

## Estrutura sugerida do repositório

```text
.
├── README.md
├── .gitignore
├── Case_H2.ipynb
└── apresentacao-analise-dados-h2.pdf
 ```

## Metodologia

A análise foi organizada em três grandes etapas:

### 1. Análise exploratória dos dados

Nesta etapa foram avaliados:

- estrutura das bases;
- tipos de dados;
- valores nulos e duplicados;
- perfil dos clientes;
- distribuição de idade e gênero;
- canais de entrada dos usuários;
- jogos mais populares;
- tipos de jogos mais jogados;
- valores apostados e ganhos;
- distribuição de depósitos e saques.

### 2. Criação de indicadores

Foram criadas métricas para comparar comportamentos entre jogadores e apoiar a identificação de padrões de risco.

Entre os principais indicadores utilizados estão:

#### Taxa de retorno por jogador

A taxa de retorno foi calculada pela razão entre o valor ganho e o valor apostado:

```text
taxa_retorno = valor_ganho / valor_apostado
```

Interpretação:

- `taxa_retorno < 1`: o jogador perdeu mais do que ganhou.
- `taxa_retorno = 1`: o jogador ficou em equilíbrio.
- `taxa_retorno > 1`: o jogador ganhou mais do que apostou.

Jogadores com taxa de retorno muito acima do comportamento geral da base podem indicar uso de estratégias específicas, exploração de padrões de determinados jogos ou possível vulnerabilidade operacional.

#### Jogos com alta taxa de retorno

Também foi calculada a taxa de retorno por jogo, permitindo identificar jogos com comportamento acima do esperado.

Esse indicador ajuda a responder perguntas como:

- Há jogos com retorno médio muito superior aos demais?
- Jogadores com alta taxa de retorno estão concentrando apostas nesses jogos?
- Determinados jogos exigem revisão de mecânica, regras ou monitoramento?

#### Razão entre saques e depósitos

A razão entre saques e depósitos foi usada para identificar movimentações financeiras potencialmente atípicas:

```text
razao_saque = total_sacado / total_depositado
```

Jogadores com razão de saque muito elevada podem exigir monitoramento adicional, principalmente quando os saques não são acompanhados por volume proporcional de apostas.

### 3. Definição de regras de risco

Foram propostas regras estatísticas para sinalizar jogadores suspeitos, como:

- jogadores com taxa de retorno acima do percentil 99 da base;
- jogadores com participação relevante em jogos de alta taxa de retorno;
- jogadores com razão de saque elevada em relação aos depósitos.

O foco foi criar uma primeira camada de monitoramento baseada em regras simples, transparentes e fáceis de explicar para áreas de negócio.

## Principais descobertas

A análise indicou três pontos principais:

1. Alguns jogadores apresentaram taxa de retorno muito acima do comportamento médio da base.
2. A regra de jogos suspeitos pode ser refinada, pois os jogadores sinalizados não estavam necessariamente concentrando 100% das apostas em jogos de alta taxa de retorno.
3. A razão entre saques e depósitos se mostrou útil para identificar movimentações financeiras atípicas.

Esses pontos indicam que a abordagem por regras é útil como primeira camada de detecção, mas pode ser aprimorada com novas métricas, validação operacional e, em uma etapa futura, modelos preditivos.

## Impacto para o negócio

Os resultados da análise podem apoiar decisões em diferentes frentes:

- **Segurança da plataforma:** identificação de jogadores com comportamento atípico.
- **Prevenção de perdas:** monitoramento de possíveis explorações de padrões de jogos.
- **Controle financeiro:** detecção de saques desproporcionais aos depósitos.
- **Produto:** revisão de jogos com retorno muito acima do esperado.
- **Operações:** criação de alertas e dashboards de acompanhamento.

## Recomendações

### Curto prazo

- Implementar alertas automáticos para jogadores com taxa de retorno atípica.
- Monitorar usuários com razão de saque elevada.
- Revisar regras de saque e depósito para casos extremos.

### Médio prazo

- Criar dashboards para acompanhamento contínuo.
- Avaliar jogos com maior taxa de retorno.
- Refinar critérios estatísticos para reduzir falsos positivos.

### Longo prazo

- Desenvolver modelos de machine learning para prever padrões de risco.
- Criar uma régua de risco com múltiplos indicadores.
- Integrar os alertas ao fluxo operacional da empresa.

## Como executar o notebook

1. Clone este repositório:

```bash
git clone https://github.com/seu-usuario/h2-poker-risk-analysis.git
cd h2-poker-risk-analysis
```

2. Crie e ative um ambiente virtual:

```bash
python -m venv .venv
```

No Windows:

```bash
.venv\Scripts\activate
```

No Linux/Mac:

```bash
source .venv/bin/activate
```

3. Instale as dependências:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

4. Adicione os arquivos de dados na pasta `data/`, mantendo os nomes esperados pelo notebook:

```text
data/
├── casino_activity.csv
├── client.csv
└── financial_activity.csv
```

5. Abra o notebook:

```bash
jupyter notebook notebooks/Case_H2.ipynb
```

## Privacidade e dados

Os arquivos de dados originais não devem ser versionados no GitHub.

Este repositório foi pensado para fins de portfólio e demonstração técnica. Antes de publicar qualquer base, tabela exportada ou print com IDs de usuários, é importante garantir que não haja exposição de dados pessoais, dados operacionais privados ou informações sensíveis da empresa.

## Possíveis melhorias futuras

- Reorganizar o notebook em funções reutilizáveis.
- Criar um pipeline em Python para execução automatizada da análise.
- Exportar os resultados para um dashboard.
- Criar um score de risco ponderado por múltiplos indicadores.
- Validar as regras com especialistas de negócio.
- Comparar a abordagem baseada em regras com modelos de machine learning.

## Autor

**Rodrigo Terra**

Físico, especialista em tecnologias educacionais e analista de dados.

- GitHub: [@rodrigorissettoterra](https://github.com/rodrigorissettoterra)
- LinkedIn: [Rodrigo Terra](https://www.linkedin.com/in/rodrigoterra/)

## Aviso

Este projeto tem finalidade educacional e de portfólio. As análises, regras e recomendações apresentadas representam uma proposta analítica baseada nos dados disponibilizados para o case e não devem ser interpretadas como acusação ou prova de fraude por parte de qualquer usuário específico.
