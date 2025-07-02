# 📦 Projeto C.U

> C.U ou Cursoso Universitarios é o tema para meu projeto. Esse projeto foi desenvolvido ao decorrer do prazo da avaliação 3 na matéria de Banco de Dados>.

---


## 📖 Sobre

**`Cursos Universitarios`** é um pequeno sistema de banco de dados que consiste no seguinte diagrama.
![estrutura correta](https://github.com/user-attachments/assets/08541dd9-99e4-4dba-bc61-af362af2dd67)
---
O DER contém as seguintes tabelas com seus relacionamentos:

- **alunos**
- **professores**
- **cursos**
- **salas**
- **matricula**

---

 Neste sistema nós armazenamos os dados não somente dos alunos, mais tabém de professores e cursos.
> Destaque para a atabela de Matricula, aonde puxando os dados dela podemos visualizar todos os dados mais importantes do aluno, do curso finalizado ou em andamento, sala e informações sobre o professor.


## 🧱 Script SQL para Criação do banco de dados

A seguir os scripts utilizados para o desenvolvimento do melhor trabalho do 3°D

### 📘 criação do banco de dados

```sql
CREATE DATABASE CursosUniversitarios;
```

O comando `CREATE DATABASE` **cria o  nosso banco de dados principal** no sistema de gerenciamento de banco de dados (SGBD).

Neste caso, o banco de dados criado se chama `CursosUniversitarios`, e ele será utilizado para armazenar todas as tabelas seguintes tabelas
### 📌 Tabela: `professores`
```sql
CREATE TABLE professores (
    ID_professor INT PRIMARY KEY,
    nome_professor VARCHAR(100),
    formação VARCHAR(255),
    ID_curso VARCHAR(255),
    salario DECIMAL,
    cursos_ID_cursos INT
);
```
Responsável por armazenar os dados dos professores.

**Campos principais:**
- `ID_professor`: identificador único do professor.
- `nome_professor`: nome completo.
- `formação`: área de formação.
- `ID_curso`: código do curso (texto).
- `salario`: valor do salário.
- `cursos_ID_cursos`: chave estrangeira para tabela `cursos`.
---
### 📌 Tabela: `cursos`
```sql
CREATE TABLE cursos (
    ID_cursos INT PRIMARY KEY,
    nome_curso VARCHAR(255),
    professor VARCHAR(100),
    cargahoraria INT,
    professores_ID_professor INT,
    FOREIGN KEY (professores_ID_professor) REFERENCES professores(ID_professor)
);
```
Responsável por armazenar os dados dos cursos oferecidos.

**Campos principais:**
- `ID_cursos`: identificador único do curso.
- `nome_curso`: nome do curso.
- `professor`: nome do professor responsável pelo curso.
- `cargahoraria`: carga horária total do curso.
- `professores_ID_professor`: chave estrangeira para tabela `professores`.
---
  ### 📌 Tabela: `alunos`
```sql
CREATE TABLE alunos (
    ID_aluno INT PRIMARY KEY,
    ID_curso VARCHAR(255),
    matricula VARCHAR(255),
    cpf INT,
    cursos_ID_cursos INT,
    FOREIGN KEY (cursos_ID_cursos) REFERENCES cursos(ID_cursos)
);
```
Responsável por armazenar os dados dos estudantes matriculados.

**Campos principais:**
- `ID_aluno`: identificador único do aluno.
- `ID_curso`: código do curso (texto).
- `matricula`: código de matrícula do aluno.
- `cpf`: número do CPF do aluno.
- `cursos_ID_cursos`: chave estrangeira para tabela `cursos`.
---
### 📌 Tabela: `salas`
```sql
CREATE TABLE salas (
    ID_salas INT PRIMARY KEY,
    relatorio TEXT,
    ultimo_usuario VARCHAR(255),
    professores_ID_professor INT,
    FOREIGN KEY (professores_ID_professor) REFERENCES professores(ID_professor)
);
```
Responsável por armazenar informações das salas utilizadas nos cursos.

**Campos principais:**
- `ID_salas`: identificador único da sala.
- `relatorio`: observações ou ocorrências registradas da sala.
- `ultimo_usuario`: último usuário que utilizou a sala.
- `professores_ID_professor`: chave estrangeira para tabela `professores`.
---
### 📌 Tabela: `matricula`
```sql
CREATE TABLE matricula (
    ID_matricula INT PRIMARY KEY,
    alunos_ID_aluno INT,
    cursos_ID_cursos INT,
    professores_ID_professor INT,
    salas_ID_salas INT,
    FOREIGN KEY (alunos_ID_aluno) REFERENCES alunos(ID_aluno),
    FOREIGN KEY (cursos_ID_cursos) REFERENCES cursos(ID_cursos),
    FOREIGN KEY (professores_ID_professor) REFERENCES professores(ID_professor),
    FOREIGN KEY (salas_ID_salas) REFERENCES salas(ID_salas)
);
```
Responsável por controlar o vínculo entre alunos, cursos, professores e salas.

**Campos principais:**
- `ID_matricula`: identificador único da matrícula.
- `alunos_ID_aluno`: chave estrangeira para tabela `alunos`.
- `cursos_ID_cursos`: chave estrangeira para tabela `cursos`.
- `professores_ID_professor`: chave estrangeira para tabela `professores`.
- `salas_ID_salas`: chave estrangeira para tabela `salas`.
---
