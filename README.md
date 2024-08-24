# Exercícios de SQL #1

## Responda as seguintes perguntas utilizando a linguagem SQL:

1. Crie uma consulta para retornar o nome distinto dos vendedores;
2. Crie uma consulta para retornar o valor total das vendas realizadas por cada vendedor, ordenando do maior valor, até o menor valor;
4. Crie uma consulta para retornar o mês e o ano em que tivemos o maior faturamento em vendas;
5. Crie uma consulta para retornar as 10 primeiras vendas que foram realizadas;
6. Crie uma consulta para retornar a quantidade de vendas para cada um dos status.

### Tópico 1:
    
    SELECT DISTINCT
        nome_vendedor
    FROM desafio_sql_1


### Tópico 2:

    SELECT
        nome_vendedor,
    SUM(valor_venda) AS total_vendas  
    FROM desafio_sql_1
    WHERE status_negociacao = 'Vendido'
    GROUP BY nome_vendedor
    ORDER BY total_vendas DESC


### Tópico 3 - 1ª solução:

    SELECT 
        MONTH(Data_venda) AS Mes,
        YEAR(Data_venda) AS Ano,
        SUM(Valor_venda) AS Total_Faturamento
    FROM desafio_sql_1
    WHERE Status_negociacao = 'Vendido'
    GROUP BY Mes
    ORDER BY Total_Faturamento DESC
    LIMIT 1

### Tópico 3 - 2ª solução:

    SELECT 
        CONCAT(MONTH(Data_venda), '-', YEAR(Data_venda)) AS Mes_Ano,
        SUM(Valor_venda) AS Total_Faturamento
    FROM desafio_sql_1
    WHERE Status_negociacao = 'Vendido'
    GROUP BY Mes_Ano
    ORDER BY Total_Faturamento DESC
    LIMIT 1


### Tópico 4:

    SELECT
        data_venda,
        valor_venda
    FROM desafio_sql_1
    WHERE status_negociacao ='Vendido'
    ORDER BY data_venda
    LIMIT 10


### Tópico 5:

    SELECT
        status_negociacao,
        COUNT(*) AS qtd_vendas
    FROM desafio_sql_1
    GROUP BY status_negociacao
    ORDER BY qtd_vendas DESC


