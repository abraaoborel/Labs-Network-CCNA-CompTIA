# 🚀 Road to CCNA & CompTIA Network+ | Portfólio de Redes

Este repositório documenta minha jornada técnica do absoluto zero ao nível avançado em Redes de Computadores. O objetivo é consolidar o conhecimento prático necessário para as certificações **Cisco CCNA (200-301)** e **CompTIA Network+**, com foco especial em segurança e automação para uma futura transição para **SecDevOps**.

## 📑 Estrutura do Repositório

A organização segue a progressão lógica dos exames oficiais, dividida em módulos:

*   **`01-fundamentals/`**: Fundamentos de rede, Modelos de referência OSI e TCP/IP, sistemas de numeração (Binário e Hexadecimal), endereçamento IPv4/IPv6 e arquitetura de hardware de dispositivos (CPU, RAM, Flash e NVRAM).
*   **`02-switching/`**: Configuração e segmentação de Redes Virtuais (VLANs), entroncamento (Trunking 802.1Q), protocolos de prevenção de loop como Spanning Tree (STP) e agregação de links com EtherChannel.
*   **`03-routing/`**: Conceitos de roteamento, rotas estáticas e dinâmicas, e implementação de OSPFv2 de área única.
*   **`04-security/`**: Implementação de segurança de porta (Port Security), Listas de Controle de Acesso (ACLs), Redes Privadas Virtuais (VPNs) e mitigação de ataques em Camada 2.
*   **`05-automation-sdn/`**: Redes Definidas por Software (SDN), formatos de dados (JSON, YAML, XML), APIs RESTful e ferramentas de gerenciamento de configuração como Ansible e Terraform.

## 🛠️ Ferramentas Utilizadas

*   **Cisco Packet Tracer**: Simulador principal para construção de redes e testes.
*   **Wireshark**: Analisador de pacotes para observar a interação real de protocolos.
*   **VirtualBox**: Ambiente de virtualização para emular servidores e sistemas finais.
*   **Cisco IOS**: Sistema operacional via CLI para configuração de dispositivos.

## 📝 Padrão de Documentação de Laboratórios

Para cada laboratório realizado, sigo este template de documentação:

1.  **Objetivo**: Descrição técnica do que está sendo configurado.
2.  **Topologia**: Diagrama visual (físico e lógico) do cenário.
3.  **Configurações**: Snippets dos comandos CLI mais relevantes.
4.  **Verificação**: Provas de funcionamento usando comandos `show`, `ping` e `traceroute`.

---
*Documentação criada como parte do meu tecnólogo em Redes de Computadores (Unicesumar) e preparação para o mercado de cibersegurança.*
