# Relatório de Configuração do Gateway com IPTables e NAT

> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson <br>
> **Aluno(a):** Maria Eduarda de Araújo Silva <br>
> **Matrícula:** 2023007122 <br>
> **Turma:** BSI 2026.02 <br>
> **Data:** 07/10/2026


## 1. Objetivo
O objetivo desta atividade foi configurar a **VM1 como gateway da rede interna**, habilitando o encaminhamento de pacotes IPv4 
e configurando regras de **NAT/MASQUERADE com IPTables**.
Também foram configuradas regras para permitir a comunicação entre a rede interna e a rede externa e a persistência das configurações 
para que fossem mantidas após a reinicialização do servidor.

## 2. Ambiente
A atividade foi realizada utilizando duas máquinas virtuais:

| Item                | VM1 — Gateway       | VM2 — Cliente       |
| ------------------- | ------------------- | ------------------- |
| Sistema operacional | Ubuntu Server 26.04 | Ubuntu Server 26.04 |
| Plataforma          | VirtualBox          | VirtualBox          |
| Função              | Gateway             | Cliente             |
| Interface interna   | `enp0s8`            | intnet              |
| Interface externa   | `enp0s3`            | -                   |
| Rede externa        | `172.20.23.13/22`   | `10.0.0.14/24`      |
| Gateway interno     | `172.20.20.1`       | `10.0.0.13`         |

## 3. Procedimento

### 3.1 Habilitação do encaminhamento IPv4

Na VM1, foi habilitado o encaminhamento de pacotes IPv4, utilizando o net.ipv4.ip_forward=1.
Além disso, foram configuradas regras de NAT para permitir que os dispositivos da rede interna utilizassem a VM1 para acessar a rede externa. <br>
Por fim, para manter as regras do IPTables após a reinicialização, foi instalado o pacote `iptables-persistent` e as regras foram salvas utilizando o comando `sudo netfilter-persistent save`.

### 3.2 Testes na VM2
Na VM2, foram realizados testes de conectividade com o gateway interno pingando para três endereços: `10.0.0.1`, `172.20.20.1`,  `1.1.1.1` <br>
Além disso, também foi testada a resolução de nomes como `nslookup google.com` e o rastreamento da rota `traceroute google.com`.

## 4. Testes e Capturas de Tela
**Figura 1 – Configuração de rede da VM1 e VM2 no VirtualBox**
<img width="647" height="296" alt="Captura de tela 2026-10-07 203954" src="https://github.com/user-attachments/assets/3fc68459-dcc6-4822-986e-6693bd2c6546" /> <br>
<img width="672" height="289" alt="Captura de tela 2026-10-07 204003" src="https://github.com/user-attachments/assets/0e02a1d8-e378-4dda-ba36-a1d186e5bcf0" /> <br>
<img width="654" height="278" alt="Captura de tela 2026-10-07 204014" src="https://github.com/user-attachments/assets/80c56263-cd27-475b-8f63-ebed19d6aa96" />

**Figura 2 – Conteúdo dos arquivos netplan em VM1 e VM2** <br>
<img width="425" height="415" alt="Captura de tela 2026-10-07 203822" src="https://github.com/user-attachments/assets/432d779c-b16c-4efd-82d9-2904d753bcf4" /> <br>
<img width="441" height="314" alt="Captura de tela 2026-10-07 203840" src="https://github.com/user-attachments/assets/15db981e-34f6-4725-b326-7239c0524ded" />

**Figura 3 – Saída de sysctl net.ipv4.ip_forward na VM1.** <br>
<img width="503" height="54" alt="Captura de tela 2026-10-07 200901" src="https://github.com/user-attachments/assets/46a09bbe-4553-43b7-8645-fe7d2df15d37" />

**Figura 4 – Saídas de sudo iptables -t nat -L -n -v e sudo iptables -L -n -v na VM1.**
<img width="959" height="452" alt="Captura de tela 2026-10-07 201911" src="https://github.com/user-attachments/assets/1ae4e874-7b8c-4d1a-a14b-137d18ad0839" />

**Figura 5 – Prints/capturas dos testes executados na VM2** <br>
<img width="539" height="499" alt="Captura de tela 2026-10-07 202906" src="https://github.com/user-attachments/assets/e14b2672-f65b-485e-b6e9-b60eba4188b2" />

## 5. Problemas e Soluções <br>

Nenhum problema foi encontrado.

## 6. Conclusão
A realização desta atividade possibilitou compreender, na prática, o funcionamento de uma máquina Linux atuando como **gateway de uma rede interna**.
Foi realizado o encaminhamento de pacotes IPv4 na VM1 e configurado o **NAT/MASQUERADE utilizando IPTables**, permitindo que a VM2 acessasse redes externas por meio do gateway.
Além disso, as regras foram persistidas utilizando o `iptables-persistent`, garantindo que a configuração permanecesse disponível após uma reinicialização do sistema. <br>
Dessa forma, os objetivos da atividade foram alcançados, proporcionando uma compreensão prática da configuração de **roteamento, NAT e encaminhamento de pacotes em um servidor Linux**.

## Referências
* https://github.com/alaelson/labredes-2026.2/blob/main/Aula8.md
