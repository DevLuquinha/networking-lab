# Lab 01 — Rede LAN da Coisa Qualquer

## Contexto

A empresa fictícia **Coisa Qualquer**, localizada em Uberaba, precisa conectar seus departamentos por meio de uma rede local. Neste laboratório, a infraestrutura será montada e configurada no Cisco Packet Tracer para permitir a comunicação entre os computadores e o uso de serviços internos da empresa.

## Estrutura da empresa

A rede deve incluir os seguintes departamentos e equipamentos:

| Departamento | Equipamentos |
|---|---|
| Recursos Humanos (RH) | 1 switch Ethernet de 24 portas e 3 PCs |
| Fiscal | 1 switch Ethernet de 24 portas e 2 PCs |
| Produção | 1 switch Ethernet de 24 portas e 2 PCs |
| Vendas | 1 switch Ethernet de 24 portas e 3 PCs |
| Tecnologia da Informação (DTI) | 1 switch Ethernet de 24 portas, 2 PCs, 1 servidor Web e 1 servidor DNS/DHCP |

Os switches departamentais devem estar interligados para formar uma única LAN da empresa.

## Requisitos

- Interligar os cinco departamentos em uma rede local funcional.
- Configurar a rede com o bloco IPv4 `192.168.1.0/24`.
- Disponibilizar DHCP e DNS em um servidor local no DTI.
- Disponibilizar um servidor Web no DTI com os serviços HTTP e HTTPS ativos.
- Permitir que todos os computadores usem o DHCP e o DNS locais e acessem o servidor Web pelo nome configurado.

## Endereçamento

Toda a LAN deve usar a rede `192.168.1.0/24`, cuja máscara é `255.255.255.0`.

Como referência para a implementação, os servidores podem usar endereços fixos:

| Dispositivo | Endereço de referência |
|---|---|
| Servidor DNS/DHCP | `192.168.1.2` |
| Servidor Web | `192.168.1.3` |

Os endereços dos PCs devem ser entregues automaticamente pelo DHCP, dentro da mesma rede. O plano deve evitar conflitos com os endereços fixos dos servidores.

## DHCP

Ative o serviço DHCP no servidor DNS/DHCP do DTI e configure um pool adequado à rede `192.168.1.0/24`. O pool deve fornecer aos clientes, no mínimo, um endereço IP, a máscara de rede e o endereço do servidor DNS local.

Todos os PCs dos departamentos devem obter sua configuração de rede por DHCP.

## DNS

Ative o serviço DNS no servidor DNS/DHCP e crie um registro que associe o domínio de exemplo `www.coisaqualquer.com.br` ao endereço IP do servidor Web.

Os computadores devem receber pelo DHCP o endereço do servidor DNS local e conseguir resolver esse nome para acessar o site interno.

## Servidor Web

Configure o servidor Web no DTI com endereço IP fixo e habilite os serviços **HTTP** e **HTTPS**. Disponibilize uma página inicial que identifique a empresa Coisa Qualquer e sua localização em Uberaba.

O site deve poder ser acessado pelos computadores da LAN usando o domínio `www.coisaqualquer.com.br` tanto por HTTP quanto por HTTPS.

## Comunicação entre departamentos

Os computadores de RH, Fiscal, Produção, Vendas e DTI devem conseguir se comunicar dentro da LAN por meio dos switches interligados. Cada departamento deve alcançar os serviços locais de DHCP, DNS e Web.

## Testes esperados

- Conferir em cada PC que o endereço IP, a máscara e o DNS foram recebidos por DHCP.
- Testar conectividade entre computadores de departamentos diferentes e com os servidores usando `ping`.
- Verificar que `www.coisaqualquer.com.br` é resolvido para o endereço do servidor Web.
- Abrir a página da empresa pelo domínio usando `http://www.coisaqualquer.com.br`.
- Abrir a página da empresa pelo domínio usando `https://www.coisaqualquer.com.br`.

## Critérios de conclusão

O laboratório estará concluído quando:

- os cinco departamentos estiverem conectados à mesma LAN;
- os PCs receberem configuração válida pelo DHCP local;
- os clientes utilizarem o DNS local e resolverem o domínio configurado;
- HTTP e HTTPS estiverem ativos no servidor Web;
- a página da empresa puder ser acessada pelo domínio a partir dos computadores da rede;
- os testes de conectividade entre departamentos e servidores apresentarem comunicação bem-sucedida.

## Tecnologias utilizadas

- Cisco Packet Tracer
- Rede Ethernet com switches
- IPv4 e máscara `/24`
- DHCP
- DNS
- HTTP e HTTPS
- `ping` para testes de conectividade

## Arquivo do laboratório

A implementação prática desta atividade está no arquivo [`coisa-qualquer.pkt`](coisa-qualquer.pkt), que contém a topologia e as configurações realizadas no Cisco Packet Tracer.
