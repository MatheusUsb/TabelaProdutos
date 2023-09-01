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

--- Fazer um trigger para que sempre que você atualizar um produto na tabela produtos, uma entrada correspondente será registrada na tabela log_produtos para rastrear as alterações. 

DELIMITER $$

CREATE TRIGGER trigger_atualizacao_produto
AFTER UPDATE ON produtos
FOR EACH ROW
BEGIN
    INSERT INTO log_produtos (
        produto_id,
        nome_anterior,
        novo_nome,
        preco_anterior,
        novo_preco,
        data_atualizacao
    ) VALUES (
        OLD.id,
        OLD.nome,
        NEW.nome,
        OLD.preco,
        NEW.preco,
        NOW()
    );
END;

$$

DELIMITER ;

--- Test Trigger later


