# Relatório de Manipulação, Edição, Permissões e Automação de Arquivos no Linux

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson <br>
> **Aluno(a):** Maria Eduarda <br>
> **Data:** 31/08/2026

## 1. Objetivo
O objetivo desta atividade foi praticar a manipulação, edição e visualização de arquivos no sistema operacional **Ubuntu Server 26.04**. Além disso, a atividade teve como objetivo compreender o funcionamento das permissões de arquivos e desenvolver scripts para automatizar a criação e o gerenciamento de usuários em lote.

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
### 3.1 Criação da lista de usuários
Foi criado o arquivo `usuarios.txt`, contendo uma lista de 20 usuários que seriam cadastrados automaticamente.
O arquivo foi criado e editado utilizando o Nano:

```bash
nano usuarios.txt
```

Foram inseridos os usuários:

```text
aluno01
.
.
.
aluno20
```

### 3.2 Criação do script para cadastro de usuários
Foi criado o arquivo `passo1_criar.sh`, responsável pela criação dos usuários em lote:

```bash
nano passo1_criar.sh
```
O script utilizado foi:

```bash
#!/bin/bash
# Script de criação de usuários em lote

for usuario in $(cat usuarios.txt); do
    echo "Processando criação do usuário: $usuario"
    sudo useradd -m -s /bin/bash $usuario
done

echo "Processo de criação concluído!"
```

O script utiliza uma estrutura de repetição `for` para percorrer cada nome presente no arquivo `usuarios.txt`. Além disso, `cat` foi utilizado para ler o conteúdo do arquivo contendo a lista de usuários.
A opção `-m` cria automaticamente o diretório pessoal do usuário e a opção `-s /bin/bash` define o Bash como interpretador de comandos padrão.

### 3.3 Criação do script para definição das senhas
Em seguida, foi criado o arquivo `passo2_senhas.sh`, responsável por definir as senhas dos usuários:

```bash
nano passo2_senhas.sh
```
O script utilizado foi:

```bash
#!/bin/bash
# Script de definição de senhas em lote

for usuario in $(cat usuarios.txt); do
    echo "Definindo senha padronizada para: $usuario"
    echo "$usuario:$usuario" | sudo chpasswd
done

echo "Todas as senhas foram atualizadas com sucesso!"
```

Nesse script, cada usuário recebeu uma senha correspondente ao seu próprio nome. O comando `chpasswd` foi utilizado para alterar senhas de forma automatizada no formato: usuario:senha.
Dessa forma, foi possível definir as senhas dos 20 usuários sem a necessidade de defini-las individualmente para cada conta.

### 3.4 Permissão de execução dos scripts
Após a criação dos scripts, foram concedidas permissões de execução dos arquivos, utilizando o comando `chmod`:
```bash
chmod +x passo1_criar.sh
chmod +x passo2_senhas.sh
```

### 3.5 Execução dos scripts
Após a concessão das permissões necessárias, os scripts foram executados:

```bash
./passo1_criar.sh
```
Realizou a criação dos 20 usuários presentes no arquivo `usuarios.txt`.

```bash
./passo2_senhas.sh
```
Realizou a definição das senhas dos usuários criados.

## 4. Capturas de Tela
**Figura 1 – Validação dos usuários criados** <br>
<img width="475" height="345" alt="image" src="https://github.com/user-attachments/assets/93759c56-1a70-4077-a907-3a3ca127544f" />

**Figura 2 – Validação dos grupos criados** <br>
<img width="459" height="349" alt="image" src="https://github.com/user-attachments/assets/eeec68c9-4c1c-4406-afde-0f3eb9102279" />

**Figura 3 – Teste de login com um usuário criado** <br>
<img width="359" height="57" alt="image" src="https://github.com/user-attachments/assets/48a48e82-39d4-410c-922e-d22af962311d" />

## 5. Conclusão
A realização desta atividade possibilitou compreender, na prática, a manipulação e a edição de arquivos no sistema operacional Linux. A criação dos scripts em Shell também demonstrou a importância da automação na administração de sistemas.
Dessa forma, os objetivos propostos foram alcançados, proporcionando uma melhor compreensão sobre a utilização do terminal Linux, a manipulação de arquivos, o gerenciamento de permissões e a automação de tarefas administrativas.

## Referências
* Material disponibilizado pelo professor: https://github.com/alaelson/labredes-2026.2/blob/main/Aula4.md

