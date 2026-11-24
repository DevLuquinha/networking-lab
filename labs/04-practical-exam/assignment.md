# Lab 04 — Simulado da prova prática de Redes

## Origem e modo de uso

Este lab adapta o arquivo `Prova pratica de redes.pdf`, disponibilizado em 24/11/2026, para uma tentativa individual no Cisco Packet Tracer **8 ou superior**. O enunciado original prevê **120 minutos**, **20 pontos** e correção sequencial: se uma etapa não funcionar, as seguintes não serão corrigidas. A prova remarcada para **08/12/2026** pode ter outro enunciado.

**Ainda não iniciado.** Quando quiser começar, diga neste chat: **“Vou iniciar a prova prática do Lab 04.”** O mentor apresentará apenas a orientação de abertura e acompanhará as evidências que você trouxer. Inicie um cronômetro de 120 minutos por conta própria e monte uma topologia nova; não reutilize o `.pkt` do Lab 03 nesta tentativa. Salve seu arquivo neste diretório com um nome escolhido por você.

Lucas se enquadra em **Transportes**, pois a lista do professor atribui esse ramo a primeiros nomes de **I a L**. Escolha **dois negócios clientes desse ramo** e dê um nome a cada um. O PDF não fornece nomes de empresas, domínios, IPs individuais, modelos de equipamentos nem conteúdo dos sites: essas escolhas fazem parte do seu projeto.

## Objetivo geral do professor

Implante um *Internet Service Provider* (ISP) para comerciantes de Feijó/AC. O ISP deve compartilhar os sites comerciais de pelo menos dois clientes, **sem que os clientes tenham acesso direto às redes uns dos outros**. Ofereça HTTP, HTTPS, DNS e DHCP e apresente a estrutura **lógica e física** no Packet Tracer.

## Etapa 1 — LAN das matrizes (5 pontos)

Monte a matriz de **cada** cliente:

| Departamento | Equipamentos e requisitos do PDF |
|---|---|
| TI (DTI) | Um servidor Web com o site da empresa acessível por IP e URL; um servidor DHCP/DNS; um switch Fast Ethernet que conecte o DTI ao restante da empresa. |
| Administrativo (ADM) | Um switch Fast Ethernet ligado ao DTI; dois PCs com IP via DHCP e acesso ao site da empresa por DNS. |
| Vendas (DVEN) | Um switch Fast Ethernet ligado ao DTI; dois PCs com IP via DHCP e acesso ao site da empresa por DNS. |

## Etapa 2 — Matriz e filial (10 pontos)

Cada cliente tem **uma única filial**, que deve acessar o HTTP/Web e o DNS da própria matriz. O DHCP da filial deve ser **local**.

- Acrescente um roteador ao DTI de cada matriz para interligá-la à sua filial.
- Em cada filial, monte um DTI com servidor DHCP, switch de interligação e roteador para a matriz.
- Monte também um único departamento na filial com um switch e dois PCs. Os PCs devem obter IP pelo DHCP local e abrir o site da matriz pelo nome resolvido no DNS da matriz.

## Etapa 3 — ISP (5 pontos)

Monte a LAN do ISP com um DTI contendo um PC, um servidor Web próprio e **outro servidor** para DNS e DHCP local. O site do ISP deve divulgar planos de acesso e valores. Inclua um switch para os dispositivos locais e os roteadores necessários para interligar o ISP aos clientes.

Configure o DNS do ISP para que os clientes acessem por URL o site do ISP e os sites dos demais clientes. Verifique também o requisito geral de que o acesso aos sites não conceda acesso direto às demais redes dos clientes. O PDF não prescreve o mecanismo para esse isolamento.

## Endereçamento obrigatório do PDF

| Organização | Segmento | Bloco |
|---|---|---|
| ISP | LAN | `10.1.1.0/24` |
| ISP | Enlaces possíveis com clientes | `10.1.2.0/30`, `10.1.3.0/30`, `10.1.4.0/30`, `10.1.5.0/30` |
| Cliente 1 | Matriz | `172.16.1.0/24` |
| Cliente 1 | Enlace matriz–filial | `172.16.3.0/30` |
| Cliente 1 | Filial | `172.16.2.0/24` |
| Cliente 2 | Matriz | `192.168.1.0/24` |
| Cliente 2 | Enlace matriz–filial | `192.168.3.0/30` |
| Cliente 2 | Filial | `192.168.2.0/24` |

Use dois dos quatro blocos possíveis de enlace ISP–cliente e registre quais escolheu. Não confunda os endereços de rede da tabela com endereços configuráveis em hosts ou interfaces.

## Entrega e critério de conclusão do lab

Apresente a topologia lógica e física no `.pkt` e mostre, para **cada** etapa, configurações e testes que comprovem os requisitos. Registre ao menos uma concessão DHCP por LAN, acesso local aos sites por IP e por URL, acesso filial–matriz por URL, acesso por URL entre clientes e ao ISP, e um teste do isolamento entre as redes de clientes. Verifique HTTP e HTTPS separadamente e anote exatamente o que a versão do Packet Tracer permitir observar. Salve a configuração dos roteadores e o `.pkt`.

Depois da tentativa, explique o trajeto de uma consulta DNS e de uma requisição Web, incluindo a resposta. Separe **observação**, **hipótese** e **conclusão** ao diagnosticar falhas. Use o [roteiro de apoio](study-path.md) e o [modelo de evidências](evidence-template.md) somente quando precisar; eles não contêm uma solução pronta.
