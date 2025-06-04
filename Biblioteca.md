
![Der Biblioteca](https://private-user-images.githubusercontent.com/125823124/451620251-26ee80f6-4161-4295-93b8-059f9e1c172a.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDkwODA4NzEsIm5iZiI6MTc0OTA4MDU3MSwicGF0aCI6Ii8xMjU4MjMxMjQvNDUxNjIwMjUxLTI2ZWU4MGY2LTQxNjEtNDI5NS05M2I4LTA1OWY5ZTFjMTcyYS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNjA0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDYwNFQyMzQyNTFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mMTAxN2UwNmQwYTNhMTMxMjA0YzlhZjk5MWE4MDBiOTE0YzM0NmM4ZTg2MjAwZjhkMWVmYTAwZGYyZTdlNTkzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.F5lya32X9mnizzwKUly7MS1kRDXQtWjmInss5MaSp68)


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
