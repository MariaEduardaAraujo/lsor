# Relatório de Acesso Remoto SSH e Diagnóstico de Rede
> **Disciplina:** LSOR <br>
> **Professor(a):** Alaelson <br>
> **Aluno(a):** Maria Eduarda <br>
> **Data:** 09/09/2026

## 1. Objetivo
O objetivo desta atividade foi configurar e testar o acesso remoto ao Ubuntu Server por meio do protocolo SSH, 
utilizando o mecanismo de redirecionamento de portas do VirtualBox em uma máquina virtual configurada com NAT.
A atividade também teve como objetivo compreender o funcionamento do NAT e observar, na prática, o estabelecimento de uma conexão SSH 
entre o computador hospedeiro e a máquina virtual.

## 2. Ambiente
A atividade foi realizada utilizando o seguinte ambiente:

| Item                        | Especificação       |
| --------------------------- | ------------------- |
| Sistema operacional Guest   | Ubuntu Server 26.04 |
| Sistema operacional Host    | Windows             |
| Plataforma de virtualização | VirtualBox          |
| Memória RAM                 | 2 GB                |
| Processadores               | 1 vCPU              |
| Armazenamento               | 32 GB               |
| Configuração de rede        | NAT                 |
| IP da máquina virtual       | 10.0.2.15           |
| Gateway                     | 10.0.2.2            |
| Porta SSH do Guest          | 22                  |
| Porta redirecionada no Host | 5222                |

## 3. Procedimento
### 3.1 Verificação da configuração de rede
Inicialmente, foi realizada a verificação do estado das interfaces de rede da máquina virtual.
Foi possível observar a interface `enp0s3` configurada utilizando DHCP e recebendo o endereço IP `10.0.2.15/24`.

### 3.2 Inspeção das interfaces com `ifconfig`
Após a instalação dos utilitários, foi executado:

```text
ifconfig
```

Na saída foi possível identificar a interface de rede `enp0s3`, responsável pela comunicação da máquina virtual com a rede.
Entre as informações observadas estavam:

* Endereço IPv4: `10.0.2.15`;
* Máscara de rede: `255.255.255.0`;
* Endereço MAC da interface virtual;
* Interface de loopback `lo`;
* Endereço de loopback: `127.0.0.1`.

### 3.3 Verificação da porta 5222 antes do redirecionamento
Antes da criação da regra de redirecionamento no VirtualBox, foi executado no PowerShell:

```text
netstat -an | findstr 5222
```

Nesse momento, nenhuma conexão aparece na porta `5222`, pois a regra de redirecionamento ainda não foi configurada.
Esse teste serviu como referência para comparar o estado da porta antes e depois da configuração do NAT.

### 3.4 Configuração do redirecionamento de portas
No VirtualBox, foi acessada a configuração da máquina virtual:
**Configurações → Rede → Adaptador 1 → Avançado → Redirecionamento de Portas**

Foi criada uma regra com os seguintes parâmetros:
| Campo               | Valor     |
| ------------------- | --------- |
| Nome                | SSH       |
| Protocolo           | TCP       |
| IP do Hospedeiro    | 127.0.0.1 |
| Porta do Hospedeiro | 5222      |
| IP do Convidado     | 10.0.2.15 |
| Porta do Convidado  | 22        |

### 3.5 Conexão remota utilizando SSH
Com o redirecionamento configurado, foi realizada a conexão utilizando:

```text
ssh -p 5222 administrador@127.0.0.1
```
Com a sessão SSH aberta, foi utilizada uma segunda janela do PowerShell para executar:
```text
netstat -an | findstr 5222
```
Isso permitiu verificar, na prática, que a conexão entre o Windows e o Ubuntu Server estava ativa.

## 4. Testes e Evidências
Foram realizados testes para comprovar o funcionamento da configuração de rede e do acesso remoto.

**Capturas de tela:**
Figura 1 – Saída do comando `ifconfig`; <img width="696" height="318" alt="ifconfig" src="https://github.com/user-attachments/assets/bc2785d1-1d88-4ea9-ac99-35dcefd3bbde" />
<br>
Figura 2 – Saída do comando `route -n`; <img width="641" height="144" alt="Captura de tela 2026-09-10 082649" src="https://github.com/user-attachments/assets/ab1a4dc4-a452-4ba1-9bc3-295c71936645" />
<br>
Figura 3 – Saída do comando `traceroute 8.8.8.8`; <br> <img width="508" height="146" alt="Captura de tela 2026-09-10 083100" src="https://github.com/user-attachments/assets/5d50e265-df86-4a59-81a1-f50c8ac4dbfa" />
<br>
Figura 4 – Saída do comando `netstat -an | findstr 5222` antes do redirecionamento; <img width="925" height="64" alt="Captura de tela 2026-09-10 084640" src="https://github.com/user-attachments/assets/937b946a-1f25-4599-8867-59109d2afcba" />
<br>
Figura 5 – Configuração da regra de redirecionamento SSH no VirtualBox; <img width="644" height="410" alt="Captura de tela 2026-09-09 212252" src="https://github.com/user-attachments/assets/a5924131-068b-47f1-8cd7-e6c4fbd129e8" />
<br>
Figura 6 – Saída do `netstat` após o redirecionamento, mostrando `LISTENING`; <img width="828" height="77" alt="Captura de tela 2026-09-10 084817" src="https://github.com/user-attachments/assets/acf4f4ff-f144-40e0-9fb8-4539b7d89946" />
<br>
Figura 7 – Conexão SSH realizada pelo PowerShell; <img width="972" height="523" alt="Captura de tela 2026-09-09 212426" src="https://github.com/user-attachments/assets/3f31e5f1-c650-4e94-809b-94c50bfb8f08" />
<br>
Figura 8 – `netstat` durante a sessão SSH, mostrando `ESTABLISHED`; <img width="810" height="123" alt="Captura de tela 2026-09-10 084855" src="https://github.com/user-attachments/assets/37867ada-5ae1-44fb-885a-25e6f94d0ef9" />
<br>
Figura 9 – Comando `w` mostrando a sessão `pts/0`. <img width="853" height="152" alt="Captura de tela 2026-09-10 084915" src="https://github.com/user-attachments/assets/cb0788da-7dcf-4871-b42f-de3339da91a4" />
<br>

## 6. Conclusão
A realização desta atividade permitiu compreender, na prática, o funcionamento do NAT em um ambiente virtualizado e sua relação com o acesso remoto por meio 
do protocolo SSH. A configuração do redirecionamento de portas demonstrou como uma conexão destinada à porta `5222` do computador hospedeiro pode ser encaminhada 
para a porta `22` da máquina virtual. A utilização do `netstat` permitiu acompanhar essa comunicação, identificando os estados `LISTENING` e `ESTABLISHED`. Por fim, o comando `w` permitiu confirmar a existência da sessão remota através da identificação do pseudo-terminal `pts/0`. 
Dessa forma, a atividade contribuiu para uma melhor compreensão do funcionamento de redes virtualizadas, diagnóstico de conexões e administração remota de servidores Linux.

## 7. Referências
* https://github.com/alaelson/labredes-2026.2/blob/main/Aula5.md.
