# Relatório de Configuração do Ubuntu Server

> **Disciplina:** LSOR
> 
> **Professor(a):** Alaelson
> 
> **Aluno(a):** Maria Eduarda
> 
> **Data:** 12/08

## 1. Objetivo

O objetivo desta atividade foi realizar a instalação e configuração do **Ubuntu Server, 26.04**, preparando um ambiente de servidor funcional para a execução das atividades propostas na disciplina.
Durante o procedimento, foram realizadas as configurações necessárias para disponibilizar o sistema operacional, verificar seu funcionamento e testar os principais recursos configurados.


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

### 3.1 Criação da máquina virtual e Instalação do Ubuntu Server

Foi criada uma máquina virtual destinada à instalação do Ubuntu Server seguindo as instruções presentes do repositório da disciplina.

Inicialmente, foi realizada a inicialização da máquina virtual utilizando a imagem ISO do Ubuntu Server.

Durante a instalação, foram configurados:

1. Idioma e layout do teclado;
2. Configuração de rede;
3. Particionamento do disco;
4. Configuração de perfil;
5. Reinicialização do sistema.

### 3.2 Atualização do sistema

Após a instalação, o sistema foi atualizado utilizando os seguintes comandos:

```bash
sudo apt-get update
```

Esses comandos foram utilizados para atualizar a lista de pacotes disponíveis e instalar as atualizações disponíveis para o sistema.

## 4. Capturas de Tela
> **Figura 1 – Tela de Partições**
>
> *[Inserir captura de tela aqui]*

> **Figura 2 – Login como administrador**
>
> *[Inserir captura de tela aqui]*

> **Figura 3 – Saída do comando sudo**
>
> *[Inserir captura de tela aqui]*

## 5. Conclusão

A realização desta atividade possibilitou a instalação e configuração do **Ubuntu Server, 26.04**, permitindo compreender, na prática, os principais procedimentos envolvidos na preparação de um ambiente de servidor.
Durante a atividade, foram realizadas as configurações necessárias para o funcionamento do sistema, além de testes para verificar a conectividade, o estado do sistema e o correto funcionamento dos recursos configurados.
Dessa forma, os objetivos propostos foram alcançados, proporcionando uma experiência prática com a administração e configuração de um sistema operacional baseado em Linux.

---

## Referências
* Material disponibilizado pelo professor: https://github.com/alaelson/labredes-2026.2/blob/main/Aula1.md
