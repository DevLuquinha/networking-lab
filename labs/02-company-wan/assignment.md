# Lab 02 — Rede WAN da Coisa Qualquer

## Contexto

A empresa fictícia **Coisa Qualquer** já possui uma rede local na matriz, em Uberaba. Agora, a filial de Sacramento precisa de uma LAN própria e de uma conexão com a matriz. Neste laboratório, a infraestrutura será ampliada no Cisco Packet Tracer para permitir a comunicação entre as duas unidades e o uso, pela filial, dos serviços da matriz.

## Estrutura da filial

A rede de Sacramento deve incluir os seguintes departamentos e equipamentos:

| Departamento | Equipamentos |
|---|---|
| Administrativo | 1 switch Ethernet de 24 portas e 8 PCs |
| Produção | 1 switch Ethernet de 24 portas e 2 PCs |
| Vendas | 1 switch Ethernet de 24 portas e 6 PCs |
| Tecnologia da Informação (DTI) | 1 switch Ethernet de 24 portas, 1 PC e 1 servidor DHCP |

Os quatro switches da filial devem formar uma LAN. A matriz mantém os equipamentos e serviços construídos no [Lab 01](../01-company-lan/assignment.md).

## Requisitos

- Conectar a matriz em Uberaba e a filial em Sacramento por meio de roteadores.
- Configurar a LAN da filial com o bloco IPv4 `192.168.2.0/24`.
- Usar o bloco `10.1.1.0/30` no enlace entre os roteadores.
- Disponibilizar DHCP local para os PCs da filial.
- Fazer os PCs da filial utilizarem o servidor DNS da matriz.
- Permitir que os PCs da filial acessem o servidor Web da matriz.
- Preservar a implementação do Lab 01 ao criar a continuação da rede.

## Endereçamento

As três redes do laboratório são:

| Rede | Bloco IPv4 |
|---|---|
| LAN da matriz, em Uberaba | `192.168.1.0/24` |
| LAN da filial, em Sacramento | `192.168.2.0/24` |
| Enlace entre os roteadores | `10.1.1.0/30` |

Planeje endereços para as interfaces dos roteadores e para o servidor DHCP da filial. Evite conflitos entre endereços fixos e os distribuídos por DHCP. Registre os endereços efetivamente usados na matriz antes de escolher os novos.

## DHCP

Configure o servidor DHCP do DTI de Sacramento para entregar aos PCs da filial endereço IP, máscara, gateway padrão e endereço do servidor DNS da matriz.

Os 17 PCs da filial devem obter sua configuração de rede por DHCP.

## DNS

Os PCs de Sacramento devem consultar o servidor DNS que já existe na matriz. Verifique que o nome `www.coisaqualquer.com.br` resolve para o endereço do servidor Web de Uberaba.

## Servidor Web

Mantenha o servidor Web da matriz com HTTP e HTTPS ativos. A página da empresa deve poder ser acessada pelos PCs da filial usando `http://www.coisaqualquer.com.br` e `https://www.coisaqualquer.com.br`.

## Comunicação entre matriz e filial

Cada LAN precisa de um gateway para alcançar a outra unidade. Configure o enlace entre os roteadores e o encaminhamento nos dois sentidos, incluindo o caminho de resposta dos servidores da matriz para os clientes da filial.

## Testes esperados

- Conferir em PCs de todos os departamentos da filial que IP, máscara, gateway e DNS foram recebidos por DHCP.
- Testar com `ping` a comunicação entre PCs da filial e com o gateway local.
- Testar a comunicação entre os roteadores pelo enlace `10.1.1.0/30`.
- Testar com `ping` o acesso da filial aos servidores da matriz por endereço IP.
- Verificar que `www.coisaqualquer.com.br` resolve para o endereço do servidor Web da matriz.
- Abrir a página da empresa pelo domínio usando HTTP e HTTPS a partir da filial.

## Critérios de conclusão

O laboratório estará concluído quando:

- os quatro departamentos de Sacramento estiverem conectados à LAN da filial;
- os 17 PCs receberem configuração válida do DHCP local;
- o enlace entre os roteadores e a comunicação entre as duas LANs funcionarem nos dois sentidos;
- os PCs da filial utilizarem o DNS da matriz e resolverem o domínio configurado;
- a página da matriz puder ser acessada pelo domínio via HTTP e HTTPS a partir da filial;
- os testes forem registrados com evidências suficientes para explicar o caminho dos dados.

## Tecnologias utilizadas

- Cisco Packet Tracer
- Rede Ethernet com switches e roteadores
- IPv4, máscaras `/24` e `/30` e roteamento
- DHCP
- DNS
- HTTP e HTTPS
- `ping` para testes de conectividade

## Arquivo do laboratório

Use uma cópia de [`coisa-qualquer.pkt`](../01-company-lan/coisa-qualquer.pkt) como ponto de partida e salve a implementação WAN em um novo arquivo `.pkt` neste diretório. O trabalho pode ser feito por etapas com o [roteiro guiado](study-path.md).
