# Lab 01: Projeto de Infraestrutura Virtualizada (Design Lógico)

## 🎯 Objetivo
Projetar uma rede segmentada para simular um ambiente corporativo real, isolando servidores de gerenciamento, serviços internos e containers via roteamento controlado.

## 🗺️ Topologia Lógica (Planejamento)
O endereçamento foi planejado para garantir escalabilidade e segurança:

| Segmento | Rede (CIDR) | Gateway | VLAN ID | Função |
| :--- | :--- | :--- | :--- | :--- |
| **Management** | 192.168.1.100/24 | .1 | 1 | Acesso ao Proxmox e WAN |
| **LAN (Trusted)** | 10.0.1.0/24 | 10.0.1.1 | 10 | Windows Server e Zabbix |
| **DMZ (Docker)** | 10.0.2.0/24 | 10.0.2.1 | 20 | Ubuntu Server e Aplicações Web |

## 🛠️ Ferramenta de Design
- **Cisco Packet Tracer**: Utilizado para validar o fluxo de dados entre sub-redes e a sintaxe dos comandos IOS antes da implantação física.

## 📂 Arquivos no Repositório
- `topology_design.pkt`: Arquivo original do Packet Tracer.
- `config_sw_principal.txt`: Backup da configuração do Switch (VLANs e Tronco).
- `config_rt_principal.txt`: Backup da configuração do Roteador (Router-on-a-Stick).

## 🧠 Decisões de Projeto

### Por que VLAN 10 (LAN) e VLAN 20 (DMZ)?
* **Segmentação e Segurança:** Criamos VLANs para dividir um switch físico em redes lógicas independentes, isolando os domínios de broadcast. Isso garante que, se um host na DMZ for comprometido, ele não consiga atacar a LAN diretamente.
* **Nomenclatura:** IDs (10, 20) seguem organização técnica. A **DMZ** (Zona Desmilitarizada) isola serviços externos de redes privadas internas (**LAN**).

### Por que esses Gateways (10.0.1.1 e 10.0.2.1)?
* **Portão de Saída:** O Default Gateway funciona como um "portal" entre redes distintas.
* Quando o `LAN-PC` (10.0.1.10) envia dados para a DMZ, ele encaminha o pacote para seu gateway (`10.0.1.1`), que realiza o roteamento inter-VLAN baseado em sua tabela de rotas.

## ✅ Validação e Testes (Inter-VLAN Routing)
Validamos a comunicação bidirecional entre os segmentos utilizando o utilitário `ping`.

**Cenário:** Origem LAN-PC (`10.0.1.10`) ➡️ Destino DMZ-PC (`10.0.2.10`).

```text
C:\>ping 10.0.2.10

Pinging 10.0.2.10 with 32 bytes of data:

Request timed out.
Reply from 10.0.2.10: bytes=32 time<1ms TTL=127
Reply from 10.0.2.10: bytes=32 time<1ms TTL=127
Reply from 10.0.2.10: bytes=32 time<1ms TTL=127

Ping statistics for 10.0.2.10:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss)
```
Obs: O teste inverso (DMZ ➡️ LAN) também foi realizado com 100% de sucesso.

## 🔍 Análise Técnica do Resultado
* **Linha de Base (Baseline):** Este log serve como referência de desempenho normal para a rede

* **Primeiro pacote (Timeout):** Comportamento esperado devido à resolução de endereço via protocolo ARP no primeiro contato.

* **TTL = 127:** O valor original (128) foi decrementado em 1 ao passar por um "salto" (hop) no roteador RT-PRINCIPAL, provando tecnicamente o roteamento ativo.
