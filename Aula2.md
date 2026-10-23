# Relatório de Criação de Usuários e Grupos

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson <br>
> **Aluno(a):** Maria Eduarda de Araújo Silva <br>
> **Matrícula:** 2023007122 <br>
> **Turma:** BSI 2026.02 <br>
> **Data:** 12/08/2026

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
| Rede                        | NAT, enp0s3, 10.0.2.15/24               |
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

**Figura 1 – Tentativa de acesso como fulano** <br>
<img width="455" height="127" alt="Captura de tela 2026-08-20 082411" src="https://github.com/user-attachments/assets/ddf0bc22-7107-43f3-9a18-f547b7a33dae" />

**Figura 2 – Tentativa de acesso como novato** <br>
<img width="358" height="95" alt="Captura de tela 2026-08-20 082442" src="https://github.com/user-attachments/assets/e16b5350-b53a-46c9-9fde-62f20807bb60" />

**Figura 3 – Exibindo participantes do grupo financeiro** <br>
<img width="479" height="65" alt="Captura de tela 2026-08-20 082536" src="https://github.com/user-attachments/assets/e114293d-33bd-452d-ae56-de8b7f657b3f" />

**Figura 4 - Realizando criação de arquivos e testes de acesso** <br>
<img width="456" height="60" alt="Captura de tela 2026-10-23 094242" src="https://github.com/user-attachments/assets/a8a7e9e3-2f27-41a3-835e-d39536891997" /> <br>
<img width="716" height="145" alt="Captura de tela 2026-10-23 094352" src="https://github.com/user-attachments/assets/b87606ee-d2f5-454d-8697-755b7c484bc8" />
<img width="485" height="108" alt="Captura de tela 2026-10-23 094432" src="https://github.com/user-attachments/assets/3e2d5e69-3cde-49c4-a373-8f0052e3362b" /> <br>
<img width="466" height="96" alt="Captura de tela 2026-10-23 094500" src="https://github.com/user-attachments/assets/f52ab1ca-4e44-461b-8199-940b24c78bc3" /> <br>
<img width="461" height="92" alt="Captura de tela 2026-10-23 094731" src="https://github.com/user-attachments/assets/705e551a-7978-45e1-8530-9164d1560c97" />

## 5. Problemas e Soluções
Nenhum problema foi encontrado durante a execução desta atividade.

## 6. Conclusão
A realização desta atividade possibilitou a criação de usuários e do grupo, permitindo compreender, na prática, os principais procedimentos envolvidos na configuração de usuários.
Durante a atividade, foram realizadas as configurações necessárias para a criação dos mesmos, além de testes para verificar o correto funcionamento dos recursos configurados.
Dessa forma, os objetivos propostos foram alcançados, proporcionando uma experiência prática com a administração e configuração de usuários em um sistema baseado em Linux.

## Referências
* Material disponibilizado pelo professor: https://github.com/alaelson/labredes-2026.2/blob/main/Aula2.md
