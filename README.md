# TabelaProdutos

CREATE TABLE produtos (
    id INT PRIMARY KEY,
    nome VARCHAR(255),
    preco DECIMAL(10, 2)
);

CREATE TABLE log_produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    produto_id INT,
    nome_anterior VARCHAR(255),
    novo_nome VARCHAR(255),
    preco_anterior DECIMAL(10, 2),
    novo_preco DECIMAL(10, 2),
    data_atualizacao TIMESTAMP
);


