# Relatório de Configuração de Rede Estática com Netplan

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson <br>
> **Aluno(a):** Maria Eduarda <br>
> **Data:** 23/09/2026

## 1. Objetivo
O objetivo desta atividade foi configurar a máquina virtual Ubuntu Server para utilizar o modo 
**Placa em Ponte (Bridge Adapter)** no VirtualBox e definir um endereço IP estático utilizando o **Netplan**.
Também foram realizados testes de conectividade entre o computador hospedeiro Windows e a 
máquina virtual Ubuntu Server, além de testes de resolução de nomes e rastreamento de rotas utilizando o comando `traceroute`.

## 2. Ambiente

A atividade foi realizada utilizando o seguinte ambiente:

| Item                         | Especificação                        |
| ---------------------------- | ------------------------------------ |
| Sistema operacional Guest    | Ubuntu Server 26.04                  |
| Sistema operacional Host     | Windows 11                           |
| Plataforma de virtualização  | VirtualBox                           |
| Memória RAM                  | 2 GB                                 |
| Processadores                | 1 vCPU                               |
| Armazenamento                | 32 GB                                |
| Configuração de rede inicial | NAT                                  |
| Configuração de rede final   | Placa em Ponte                       |
| Rede do laboratório          | `172.20.20.0/22`                     |
| Gateway                      | `172.20.20.1`                        |
| DNS                          | `172.20.20.1`, `1.1.1.1` e `8.8.8.8` |
| IP da VM                     | `172.20.23.13/22`                    |

## 3. Procedimento

Após a configuração da placa em modo bridge e da escolha do endereço IP, foram realizados os seguintes procedimentos: 

### 3.1 Configuração do Netplan
No Ubuntu Server, foi editado o arquivo:

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

Foi configurado o endereço IP estático, o gateway e os servidores DNS. 
Após a edição, o conteúdo foi verificado e a configuração foi aplicada.
Por fim, foi verificado o endereço atribuído à interface

### 3.2 Testes de conectividade

Após a aplicação da configuração, foram realizados testes de comunicação entre o Windows e o Ubuntu Server.

No Windows, foi utilizado:

```powershell
ping 172.20.23.13
```

Na máquina virtual, foi realizado o teste em direção ao endereço IP do computador hospedeiro:

```bash
ping -c 4 172.20.21.193
```

Também foram realizados testes de rastreamento de rota:

```bash
traceroute google.com
```

e:

```bash
traceroute one.one.one.one
```

## 4. Testes e Evidências

**Figura 1 – Teste de disponibilidade do endereço IP no Windows**

<img width="612" height="404" alt="Captura de tela 2026-09-23 195702" src="https://github.com/user-attachments/assets/4a134650-ff90-450d-86c5-dd81dd0ad607" />

**Figura 2 – Configuração do Adaptador de Rede no VirtualBox**

<img width="629" height="267" alt="Captura de tela 2026-09-23 195720" src="https://github.com/user-attachments/assets/eaab97e7-85bf-4080-a489-6ba33e7cad72" />

**Figura 3 – Conteúdo do arquivo `00-installer-config.yaml`**

<img width="557" height="320" alt="Captura de tela 2026-09-23 200145" src="https://github.com/user-attachments/assets/bb156122-0bda-47cf-ac60-1fe94852b31f" />

**Figura 4 – IP atribuído à interface `enp0s3`**

<img width="832" height="147" alt="Captura de tela 2026-09-23 200529" src="https://github.com/user-attachments/assets/52049533-33fe-4db4-8d48-2c6074338aa1" />

**Figura 5 – Teste de conectividade do Host para a VM**

<img width="600" height="323" alt="Captura de tela 2026-09-23 200604" src="https://github.com/user-attachments/assets/af8698c2-9e2d-45a8-9b91-c150f5efd500" />

**Figura 6 – Teste de conectividade da VM para o Host**

<img width="580" height="90" alt="Captura de tela 2026-09-23 201251" src="https://github.com/user-attachments/assets/f83da820-dd8e-43ef-9136-75a9668d0515" />

**Figura 7 – `traceroute google.com`**

<img width="719" height="172" alt="Captura de tela 2026-09-23 201342" src="https://github.com/user-attachments/assets/89911c3e-6be5-4588-bf83-369c3f723e8d" />

**Figura 8 – `traceroute one.one.one.one`**

<img width="707" height="165" alt="Captura de tela 2026-09-23 201448" src="https://github.com/user-attachments/assets/5249ac2c-f11b-4408-a4c2-805292ebfefd" />

## 5. Conclusão
A realização desta atividade possibilitou compreender, na prática, a configuração de uma máquina virtual em modo **Placa em Ponte**, permitindo sua participação direta na rede física do laboratório.
Também foi realizada a configuração de um endereço IP estático utilizando o **Netplan**, incluindo a definição da máscara de rede, gateway e servidores DNS. 
Dessa forma, os objetivos da atividade foram alcançados, contribuindo para a compreensão da configuração de redes estáticas e do funcionamento de máquinas virtuais conectadas diretamente a uma rede local.

## Referências
* https://github.com/alaelson/labredes-2026.2/blob/main/Aula6.md
