![Der Festa](https://private-user-images.githubusercontent.com/125823124/451619232-d99899ba-04d7-48ca-9a73-21a89a438d8f.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDkwODA0ODEsIm5iZiI6MTc0OTA4MDE4MSwicGF0aCI6Ii8xMjU4MjMxMjQvNDUxNjE5MjMyLWQ5OTg5OWJhLTA0ZDctNDhjYS05YTczLTIxYTg5YTQzOGQ4Zi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNjA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDYwNFQyMzM2MjFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iMzQxMjc5ZGNiMzk2YjljZmM3YWZjYjk0NzE3MmE2OTA4YzRjMTY3NjBiZTg0Yzk2N2MxMWUzNDMxYmRmNGNhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.WDgLfEg_DRBhGRumzo_Wcpbq-_3AGPMRyweFxMLe6BQ)


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
