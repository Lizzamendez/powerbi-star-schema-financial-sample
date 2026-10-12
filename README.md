# Modelagem Dimensional (Star Schema) no Power BI – Financial Sample

Projeto desenvolvido como desafio da DIO. A partir da tabela única **Financial Sample**,
construí um modelo dimensional em **star schema** no Power BI, separando os dados em
tabelas dimensão e uma tabela fato.

## Objetivo

Transformar uma tabela plana em um modelo organizado, mais fácil de manter, mais
performático e pronto para análises de vendas.

## Estrutura do repositório

├── powerbi/        # Arquivo .pbix do projeto
├── docs/           # Imagem do esquema em estrela
└── README.md

## Modelo de dados

![Star Schema](docs/star-schema.png)

| Tabela | Tipo | Descrição |
|---|---|---|
| Financials_origem | Backup (oculta) | Cópia da tabela original, sem alterações |
| D_Produtos | Dimensão | ID, nome do produto e estatísticas de vendas (média, mediana, máximo e mínimo) |
| D_Produtos_Detalhes | Dimensão | Discount Band, Sale Price, Units Sold e Manufacturing Price |
| D_Descontos | Dimensão | Desconto e faixa de desconto por produto |
| D_Detalhes | Dimensão | Informações adicionais de vendas não contempladas nas outras dimensões |
| D_Calendário | Dimensão | Tabela de datas criada com DAX |
| F_Vendas | Fato | Métricas e chaves de vendas (Units Sold, Sales Price, Profit, Date…) |

## Processo de construção

1. **Importação:** carreguei a base Financial Sample no Power BI.
2. **Backup:** mantive `Financials_origem` oculta como cópia de segurança.
3. **Power Query:** criei as tabelas dimensão a partir de referências da tabela original,
   selecionando apenas as colunas necessárias e removendo duplicatas.
4. **Agrupamento:** criei `D_Produtos` agrupando por produto para calcular média, mediana,
   máximo e mínimo.
5. **Coluna condicional:** criei o "Índice de Produtos" com coluna condicional.
6. **Tabela fato:** montei `F_Vendas` com a chave substituta (SK_ID) e as chaves das dimensões.
7. **Calendário:** criei `D_Calendário` com DAX.
8. **Relacionamentos:** relacionei as dimensões à tabela fato (1:N).
9. **Organização:** reorganizei as colunas de cada tabela.

## Funções e recursos utilizados

- **DAX:** `CALENDAR()`, (adicione aqui as demais que usar: `YEAR()`, `MONTH()`, etc.)
- **Power Query:** agrupar por, coluna condicional, remover duplicatas, mesclar consultas
- **Modelagem:** star schema, chave substituta, relacionamentos 1:N

## Como usar

1. Baixe o arquivo `.pbix` na pasta `powerbi/`.
2. Abra no Power BI Desktop.
3. Explore o modelo na aba **Modelo**.

## Aprendizados

(Escreva aqui o que aprendeu com o projeto.)

## Autor

(Seu nome) – [LinkedIn](#) | [GitHub](#)
