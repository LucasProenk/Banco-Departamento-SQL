# Sistema de Gerenciamento de Departamentos, Funcionários e Projetos

Este projeto apresenta a criação de um banco de dados relacional utilizando **Oracle SQL**, com foco na modelagem de entidades e aplicação de **restrições (constraints)** para garantir a integridade dos dados.

## 📌 Objetivo

O objetivo deste banco de dados é gerenciar informações de:

* **Departamentos**
* **Funcionários**
* **Projetos**

Cada funcionário pertence a um departamento e cada projeto também está associado a um departamento.

## 🗂 Estrutura do Banco de Dados

O banco possui **3 tabelas principais**:

### 1. DEPARTAMENTO

Armazena informações sobre os departamentos da organização.

**Campos:**

* `IDDEP` – Identificador do departamento (Primary Key)
* `NOME` – Nome do departamento
* `LOCALIZACAO` – Localização do departamento
* `ORCAMENTO` – Orçamento disponível para o departamento

**Restrições:**

* `PRIMARY KEY (IDDEP)`
* `CHECK (ORCAMENTO > 0)`

---

### 2. FUNCIONARIO

Armazena informações sobre os funcionários da empresa.

**Campos:**

* `IDFUNC` – Identificador do funcionário (Primary Key)
* `NOME` – Nome do funcionário
* `CARGO` – Cargo do funcionário
* `SALARIO` – Salário do funcionário
* `DATAADM` – Data de admissão
* `IDDEP` – Departamento ao qual o funcionário pertence
* `STATUS` – Situação do funcionário (Ativo ou Inativo)

**Restrições:**

* `PRIMARY KEY (IDFUNC)`
* `FOREIGN KEY (IDDEP)` referenciando `DEPARTAMENTO(IDDEP)`
* `CHECK (SALARIO > 0)`
* `CHECK (STATUS IN ('A','I'))`
* `DEFAULT 'A'` para o campo STATUS

---

### 3. PROJETO

Armazena informações sobre projetos da empresa.

**Campos:**

* `IDPROJ` – Identificador do projeto (Primary Key)
* `NOMEPROJ` – Nome do projeto
* `DATAINICIO` – Data de início do projeto
* `DATAFIM` – Data de término do projeto
* `IDDEP` – Departamento responsável pelo projeto

**Restrições:**

* `PRIMARY KEY (IDPROJ)`
* `FOREIGN KEY (IDDEP)` referenciando `DEPARTAMENTO(IDDEP)`

---

## 🔗 Relacionamentos

O modelo possui os seguintes relacionamentos:

* Um **Departamento** pode ter **vários Funcionários**
* Um **Departamento** pode ter **vários Projetos**

```
DEPARTAMENTO
     │
     ├── FUNCIONARIO
     │
     └── PROJETO
```

---

## 🛠 Tecnologias Utilizadas

* **Oracle Database**
* **SQL (DDL – Data Definition Language)**

---

## 📚 Conceitos Aplicados

* Modelagem de banco de dados relacional
* Criação de tabelas com `CREATE TABLE`
* Uso de **constraints**:

  * `PRIMARY KEY`
  * `FOREIGN KEY`
  * `CHECK`
  * `NOT NULL`
  * `DEFAULT`

---

## 👨‍💻 Autor

Lucas Antunes
Estudante de programação e desenvolvimento de software.
