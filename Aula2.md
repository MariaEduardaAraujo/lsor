# Relatório de Criação de Usuários e Grupos

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson<br>
> **Aluno(a):** Maria Eduarda<br>
> **Data:** 12/08

## 1. Objetivo
O objetivo desta atividade foi realizar a *criação de grupos, usuários e a concessão de permissões*. Durante a prática, foram realizadas atividades de criação e gerenciamento de usuários, organização de usuários em grupos, criação de diretórios compartilhados e configuração de permissões utilizando a notação simbólica e octal. Também foram utilizados os comandos chown, chgrp e chmod para controlar a posse e o acesso aos recursos do sistema.

## 2. Ambiente
A atividade foi realizada utilizando o seguinte ambiente:

| Item                        | Especificação                           |
| --------------------------- | --------------------------------------- |
| Sistema operacional         | Ubuntu Server 26.04                     |
| Plataforma de virtualização | VirtualBox                              |
| Memória RAM                 | 2 GB                                    |
| Processadores               | 1 vCPUs                                 |
| Armazenamento               | 32 GB                                   |
| Rede                        | -                                       |
| Computador hospedeiro       | Windows 11                              |

## 3. Procedimento

### 3.1 Criação e configuração de usuários e grupos
Foram criados os usuários fulano, cicrano, beltrano e novato. Em seguida, foi criado o grupo devs, ao qual foram adicionados apenas os três primeiros usuários.

### 3.2 Configuração de permissões
Foi criado o diretório /srv/projeto, cujo proprietário foi definido como administrador e o grupo como devs. Foram configuradas as permissões 770 para o diretório e 660 para o arquivo config_redes.txt, garantindo acesso de leitura e escrita aos membros autorizados.

### 3.3 Testes de acesso
Foram realizados testes com os usuários fulano e novato. O primeiro conseguiu acessar e modificar os arquivos por pertencer ao grupo devs, enquanto o segundo teve o acesso negado.

### 3.4 Grupo financeiro
Por fim, foi criado o grupo financeiro, com a inclusão dos usuários cicrano e beltrano, sendo realizados testes para verificar o funcionamento das permissões de acesso.

## 4. Capturas de Tela
Figura 1 – Tentativa de acesso como fulano
<img width="697" height="133" alt="Captura de tela 2026-08-19 211407" src="https://github.com/user-attachments/assets/250e84f1-a5b7-4cfe-9e71-0721754f1120" />
Figura 2 – Tentativa de acesso como novato

Figura 3 – Criação do grupo financeiro

## 5. Conclusão
A realização desta atividade possibilitou a criação de usuários e do grupo, permitindo compreender, na prática, os principais procedimentos envolvidos na configuração de usuários.
Durante a atividade, foram realizadas as configurações necessárias para a criação dos mesmos, além de testes para verificar o correto funcionamento dos recursos configurados.
Dessa forma, os objetivos propostos foram alcançados, proporcionando uma experiência prática com a administração e configuração de usuários em um sistema baseado em Linux.

## Referências
* Material disponibilizado pelo professor: https://github.com/alaelson/labredes-2026.2/blob/main/Aula2.md
