# Relatório de Estrutura de Diretórios e Permissões Avançadas no Ubuntu Server

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson <br>
> **Aluno(a):** Maria Eduarda <br>
> **Data:** 19/08 <br>

## 1. Objetivo
O objetivo desta atividade foi compreender a estrutura de diretórios do Linux, seguindo o padrão **Filesystem Hierarchy Standard (FHS)**, além de praticar a criação de estruturas de diretórios, gerenciamento de grupos e configuração de permissões de acesso.
Também foram realizados testes de isolamento entre diferentes departamentos, utilizando grupos e permissões, além da aplicação dos comandos vistos na aula anteriror (`chown`, `chmod`, `mkdir -p`, `su` e `su -`).

## 2. Ambiente
A atividade foi realizada utilizando o seguinte ambiente:

| Item                        | Especificação       |
| --------------------------- | ------------------- |
| Sistema operacional         | Ubuntu Server 26.04 |
| Plataforma de virtualização | VirtualBox          |
| Memória RAM                 | 2 GB                |
| Processadores               | 1 vCPU              |
| Armazenamento               | 32 GB               |
| Rede                        | -                   |
| Computador hospedeiro       | Windows 11          |

## 3. Procedimento
### 3.1 Estrutura do sistema
Foram explorados diretórios do Linux conforme o padrão FHS, utilizando comandos como `cd`, `ls`, `pwd` e `tail` para visualizar sua organização e arquivos de log.
OBS: O comando tail exibe as últimas linhas de um arquivo (10, por padrão).

### 3.2 Criação dos diretórios e grupos
Foi criada uma estrutura departamental em `/srv`, contendo os diretórios de Tecnologia e Vendas. Também foram criados os grupos `ti-group` e `vendas-group`, com seus respectivos usuários.

### 3.3 Configuração de permissões
Os diretórios foram associados aos respectivos grupos e configurados com permissão `770`. Também foi criado um arquivo no departamento de Tecnologia com permissão `660`, garantindo leitura e escrita apenas ao proprietário e ao grupo.

### 3.4 Testes de acesso
Foram realizados testes com diferentes usuários para verificar o isolamento entre os departamentos. Usuários pertencentes aos grupos tiveram acesso permitido, enquanto usuários externos (novato) receberam **Permission denied**.

### 3.5 Grupo Diretoria
Por fim, foi criada uma estrutura para o departamento de Diretoria, com o grupo `diretoria-group`, permissões específicas e testes de acesso para validar o controle de usuários autorizados e não autorizados.

## 4. Testes e Capturas de Tela
Figura 1 – Acesso permitido ao departamento de Tecnologia: <br>
<img width="622" height="87" alt="Captura de tela 2026-08-20 100610" src="https://github.com/user-attachments/assets/01b61eb4-1cff-4c1c-942e-763a594252b3" />

Figura 2 – Acesso negado ao departamento de Tecnologia: <br>
<img width="349" height="54" alt="Captura de tela 2026-08-20 100706" src="https://github.com/user-attachments/assets/f21aba91-aeb9-479d-9daa-e602ab104c91" />

Figura 3 – Testes de acesso ao diretório da Diretoria: <br>
<img width="423" height="73" alt="Captura de tela 2026-08-20 101229" src="https://github.com/user-attachments/assets/ce82a265-2449-4802-873a-7d75131fa3a3" /><br>
<img width="400" height="53" alt="Captura de tela 2026-08-20 101255" src="https://github.com/user-attachments/assets/d1a7fd9e-9ef8-4441-8c0b-13bf747deba1" />


## 5. Conclusão
A realização desta atividade possibilitou compreender a organização dos diretórios do Linux segundo o padrão FHS e aplicar, na prática, conceitos de administração e segurança de arquivos e diretórios. A utilização do `su -` permitiu compreender a importância de realizar testes em um ambiente de login adequado. Dessa forma, os objetivos da atividade foram alcançados, reforçando os conhecimentos relacionados à organização do sistema de arquivos e ao controle de acesso em servidores Linux.

## Referências
* Material disponibilizado pelo professor — Aula 3: https://github.com/alaelson/labredes-2026.2/blob/main/Aula3.md
