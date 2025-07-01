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

 Neste sistema nós armazenamos os dados não somente dos alunos, mais tabém de professores e curoso.
> Destaque para a atabela de Matricula, aonde puxando os dados dela podemos visualizar todos os dados mais importantes do aluno, do curso finalizado ou em andamento, sala e informações sobre o professor.

## 🧱 Script SQL para Criação das Tabelas

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
### 📌 Tabela: `Cursos`
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
Responsável por armazenar os dados dos Cursos.

**Campos principais:**
Armazena os dados dos cursos disponíveis.

Campos principais:

ID_cursos: identificador único do curso.

nome_curso: nome do curso.

professor: nome do professor responsável.

cargahoraria: carga horária total do curso.

professores_ID_professor: chave estrangeira para tabela professores.
  
