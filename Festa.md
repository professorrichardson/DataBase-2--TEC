``` sql

CREATE DATABASE IF NOT EXISTS festa_eventos;
USE festa_eventos;

-- Tabela Cliente
CREATE TABLE Cliente (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    telefone VARCHAR(20)
);

-- Tabela Festa
CREATE TABLE Festa (
    id_festa INT AUTO_INCREMENT PRIMARY KEY,
    tipo VARCHAR(50) NOT NULL,
    data DATE NOT NULL,
    local VARCHAR(100) NOT NULL,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente)
);

-- Tabela Pagamento (Entidade Fraca)
CREATE TABLE Pagamento (
    id_pagamento INT AUTO_INCREMENT PRIMARY KEY,
    valor DECIMAL(10,2) NOT NULL,
    forma_pagamento ENUM('boleto', 'cartao_credito', 'pix') NOT NULL,
    id_festa INT NOT NULL,
    FOREIGN KEY (id_festa) REFERENCES Festa(id_festa)
);

-- Tabelas de especialização de Pagamento

-- Cartão de Crédito (Especialização)
CREATE TABLE Cartao_Credito (
    id_pagamento INT PRIMARY KEY,
    nome_titular VARCHAR(100) NOT NULL,
    cpf_titular CHAR(11) NOT NULL,
    validade DATE NOT NULL,
    FOREIGN KEY (id_pagamento) REFERENCES Pagamento(id_pagamento)
);

-- Boleto (Especialização)
CREATE TABLE Boleto (
    id_pagamento INT PRIMARY KEY,
    codigo_barras VARCHAR(100) NOT NULL,
    vencimento DATE NOT NULL,
    FOREIGN KEY (id_pagamento) REFERENCES Pagamento(id_pagamento)
);

-- Pix (Especialização)
CREATE TABLE Pix (
    id_pagamento INT PRIMARY KEY,
    chave_pix VARCHAR(100) NOT NULL,
    FOREIGN KEY (id_pagamento) REFERENCES Pagamento(id_pagamento)
);
```
