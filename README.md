Sistema de Gestão de Vendas de Celulares

Aluno: Geraldo Sense
IP da API: 127.0.0.1
Porta utilizada: 5000

1. Descrição da Aplicação

Este projeto é um sistema de gestão de vendas de celulares com CRUD completo utilizando C++ e SQLite. A aplicação permite:

Registrar compras e vendas de celulares.
Controlar estoque atual de cada modelo.
Calcular lucro unitário de cada produto.
Integrar com a API do Aldir para sincronização de dados.

A aplicação é organizada em tabelas relacionadas para fornecer informações completas sobre produtos, compras, vendas e estoque.

2. Estrutura das Tabelas
Tabela Produtos
| ID   | Marca       | Modelo        | Data da Compra | Fornecedor    |
| ---- | ----------- | ------------- | -------------- | ------------- |
| C001 | iPhone      | iPhone 14 Pro | 10/05/2023     | Apple Store   |
| C002 | Xiaomi      | Redmi Note 12 | 15/04/2023     | TechWorld     |
| C003 | Oppo        | Find X5       | 01/03/2023     | Oppo Official |
| C004 | Itel        | Itel A48      | 05/07/2023     | Mobile Hub    |
| C005 | Tecno Spark | Spark 10 Pro  | 20/12/2022     | TechSupply    |

Tabela Compras
| Preço de Compra | Quantidade Comprada | Data da Venda | Cliente        |
| --------------- | ------------------- | ------------- | -------------- |
| 1199.00€        | 10                  | 01/06/2023    | John Doe       |
| 250.00€         | 20                  | 20/05/2023    | Maria Silva    |
| 900.00€         | 8                   | 10/04/2023    | Carlos Pereira |
| 80.00€          | 30                  | 20/07/2023    | Ana Costa      |
| 150.00€         | 15                  | 15/01/2023    | Luis Gomez     |

Tabela de vendas
| Preço de Venda | Quantidade Vendida | Estoque Atual | Lucro Unitário |
| -------------- | ------------------ | ------------- | -------------- |
| 1299.00€       | 5                  | 5             | 100.00€        |
| 300.00€        | 12                 | 8             | 50.00€         |
| 950.00€        | 4                  | 4             | 50.00€         |
| 100.00€        | 20                 | 10            | 20.00€         |
| 180.00€        | 10                 | 5             | 30.00€         |

3. Endpoints Principais

A API REST oferece os seguintes endpoints:
| Método | Endpoint         | Descrição                  |
| ------ | ---------------- | -------------------------- |
| GET    | `/produtos`      | Retorna todos os produtos  |
| GET    | `/produtos/{id}` | Retorna produto específico |
| POST   | `/produtos`      | Adiciona novo produto      |
| PUT    | `/produtos/{id}` | Atualiza produto existente |
| DELETE | `/produtos/{id}` | Remove produto             |
| GET    | `/compras`       | Lista todas as compras     |
| POST   | `/compras`       | Registra nova compra       |
| GET    | `/vendas`        | Lista todas as vendas      |
| POST   | `/vendas`        | Registra nova venda        |
| GET    | `/estoque`       | Mostra estoque atual       |

4. Exemplos de Requisições JSON
Adicionar Produto
POST /produtos
{
  "id": "C006",
  "marca": "Samsung",
  "modelo": "Galaxy S23",
  "data_compra": "01/01/2024",
  "fornecedor": "Samsung Store"
}
Registrar Compra
POST /compras
{
  "produto_id": "C006",
  "preco_compra": 1200.00,
  "quantidade_comprada": 10,
  "data_venda": "15/01/2024",
  "cliente": "Ana Martins"
}
Registrar Venda
POST /vendas
{
  "produto_id": "C006",
  "preco_venda": 1350.00,
  "quantidade_vendida": 5
}
5. Comunicação com API do Aldir

A integração com a API do Aldir permite sincronização dos dados de produtos, compras e vendas:

Base URL da API do Aldir: [https://api.aldir.com.br](https://api.aldir.com.br)
Endpoint exemplo: /produtos/sincronizar
Requisição:
POST /produtos/sincronizar
{
  "produto_id": "C001",
  "marca": "iPhone",
  "modelo": "iPhone 14 Pro",
  "estoque": 5
}
