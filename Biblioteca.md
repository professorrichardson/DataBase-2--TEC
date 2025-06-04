``` sql
CREATE  DATABASE  IF  NOT  EXISTS biblioteca;

USE biblioteca;

  
  

CREATE  TABLE  Autor (

id_autor INT AUTO_INCREMENT PRIMARY KEY,

nome VARCHAR(100) NOT NULL,

nacionalidade VARCHAR(50)

);

  

CREATE  TABLE  Livro (

id_livro INT AUTO_INCREMENT PRIMARY KEY,

titulo VARCHAR(150) NOT NULL,

ano_publicacao YEAR,

isbn VARCHAR(20)

);

  

-- Tabela associativa para o relacionamento N:M entre Livro e Autor

CREATE  TABLE  Livro_Autor (

id_livro INT,

id_autor INT,

PRIMARY KEY (id_livro, id_autor),

FOREIGN KEY (id_livro) REFERENCES Livro(id_livro),

FOREIGN KEY (id_autor) REFERENCES Autor(id_autor)

);

  

CREATE  TABLE  Aluno (

id_aluno INT AUTO_INCREMENT PRIMARY KEY,

nome VARCHAR(100) NOT NULL,

matricula VARCHAR(20) UNIQUE  NOT NULL,

curso VARCHAR(100)

);

  

CREATE  TABLE  Emprestimo (

id_emprestimo INT AUTO_INCREMENT PRIMARY KEY,

data_emprestimo DATE  NOT NULL,

data_devolucao DATE,

id_aluno INT  NOT NULL,

id_livro INT  NOT NULL,

FOREIGN KEY (id_aluno) REFERENCES Aluno(id_aluno),

FOREIGN KEY (id_livro) REFERENCES Livro(id_livro)

);
```
