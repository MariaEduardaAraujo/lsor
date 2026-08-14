# Relatório de Criação de Usuários e Grupos

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson<br>
> **Aluno(a):** Maria Eduarda<br>
> **Data:** 12/08

## 1. Objetivo
O objetivo desta atividade foi realizar a criação de grupos, usuários e a concessão de permissões. Durante o procedimento, foram realizadas as configurações 
necessárias para criar o grupo devs e, posteriormente, o grupo financeiro, criar quatro usuários e distribuir permissões de leitura e escrita.

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

### 3.1 Criação de Usuários e grupo
Foram criados quatro usuários seguindo as instruções presentes do repositório da disciplina.
Além disso, foi criado o grupo devs e um diretório de trabalho nomeado de /srv/projeto.

### 3.2 Mudança de dono e permissões
Após a criação do repositório de trabalho foi realizado o processo de mudança do owner, com o comando:
```bash
sudo chown administrador /srv/projeto
```
E o grupo devs foi atribuído a esse repositório, com o comando:
```bash
sudo chgrp devs /srv/projeto
```
Posteriormente, foram adicionadas permissões de leitura e escrita para o dono e o grupo:
```bash
sudo chmod 770 /srv/projeto
```

## 4. Conclusão
A realização desta atividade possibilitou a criação de usuários e do grupo, permitindo compreender, na prática, os principais procedimentos envolvidos na configuração de usuários.
Durante a atividade, foram realizadas as configurações necessárias para a criação dos mesmos, além de testes para verificar o correto funcionamento dos recursos configurados.
Dessa forma, os objetivos propostos foram alcançados, proporcionando uma experiência prática com a administração e configuração de usuários em um sistema baseado em Linux.

## Referências
* Material disponibilizado pelo professor: https://github.com/alaelson/labredes-2026.2/blob/main/Aula2.md
