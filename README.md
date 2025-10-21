# 💼 Projeto RH - Sistema de Controle de Funcionários e Salários (SQL Server)

## 🧾 Descrição
Este projeto implementa um sistema de **Gestão de Recursos Humanos (RH)** desenvolvido em **SQL Server (T-SQL)**.  
O sistema gerencia cargos, **funcionários e históricos de reajustes salariais**, com **triggers automáticas** que garantem a integridade dos dados nas operações de atualização e inserção.

---

## 🗂 Estrutura de Arquivos

| Arquivo                       | Descrição                                                                                  |
|-------------------------------|--------------------------------------------------------------------------------------------|
| `01_create_tables.sql`        | Criação do banco de dados e das tabelas principais (`CARGO`, `EMPREGADO`, `HIST_SALARIO`). |
| `02_insert_data.sql`          | Inserção de dados iniciais nas tabelas.                                                    |
| `03_trigger_hist_salario.sql` | Trigger que grava automaticamente o histórico de reajustes salariais.                      |
| `04_trigger_valida_faixa.sql` | Trigger que valida o salário conforme a faixa mínima e máxima definida no cargo.           |
| `05_consultas.sql`            | Consultas SQL de teste e demonstração dos resultados.                                      |

---

## ⚙️ Funcionalidades Principais

### 🔹 1. Controle de Faixa Salarial
A trigger `FAIXA_SALARIO` impede que um funcionário seja inserido ou atualizado com salário fora dos limites definidos para o seu cargo:
- Exibe erro `"SALARIO MENOR QUE O PISO"` se o valor for menor que o mínimo.
- Exibe erro `"SALARIO MAIOR QUE O TETO"` se o valor for maior que o máximo.

### 🔹 2. Histórico de Reajustes
A trigger `HISTORICO_SALARIO` registra automaticamente toda alteração no salário de um funcionário, armazenando:
- ID do funcionário
- Salário antigo
- Salário novo
- Data da alteração

---

## 🧩 Consultas de Demonstração
**Histórico de reajustes recentes:**
```sql
SELECT TOP 10 *
FROM HIST_SALARIO
ORDER BY DATA_ALTERACAO DESC;
```

**Funcionários e seus cargos:**
```sql
SELECT E.NOME, C.NOME_CARGO, E.SALARIO_ATUAL
FROM EMPREGADO E
INNER JOIN CARGO C ON E.ID_CARGO = C.IDCARGO;
```

## 🚀 Como Executar o Projeto
1. Execute o script 01_create_tables.sql no SQL Server Management Studio (SSMS) ou VS Code com extensão de SQL.
2. Execute o script 02_insert_data.sql para inserir dados de exemplo.
3. Execute os scripts 03_trigger_hist_salario.sql e 04_trigger_valida_faixa.sql para criar as triggers.
4. Utilize 05_consultas.sql para visualizar os resultados e testar as validações.

## 🧠 Tecnologias Utilizadas
- SQL Server 2022 (T-SQL)
- Visual Studio Code (edição dos scripts)
- Git e GitHub (versionamento e portfólio)

## 🎯 Objetivos do Projeto
- Praticar modelagem de banco de dados relacional
- Criar e aplicar triggers para validação e histórico
- Entender o controle de integridade referencial
- Estruturar um projeto SQL completo e profissional para portfólio

## ✍️ Autor
Guilherme de Souza Krauss 

📧 gui.skrauss@gmail.com

💼 LinkedIn: www.linkedin.com/in/guilherme-krauss
 | GitHub: https://github.com/GuilhermeKrauss

⚖️ Licença
Este projeto está licenciado sob a MIT License — veja o arquivo LICENSE para mais detalhes.
