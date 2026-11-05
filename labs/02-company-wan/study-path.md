# Roteiro guiado — Lab 02: rede WAN

Avance **uma etapa por vez** com o mentor. Antes de cada etapa, você pode pedir pesquisa guiada sobre o conceito envolvido. Faça uma previsão, configure, observe e explique; leve ao chat saídas e capturas quando algo divergir. Guarde o [Lab 01](../01-company-lan/coisa-qualquer.pkt) sem alterações e salve sua continuação WAN em um novo arquivo `.pkt` neste diretório quando começar a montar a topologia.

| Etapa | Conceito e tarefa | Evidência para seguir adiante |
|---|---|---|
| 1. Conferir o ponto de partida | Identificar as duas LANs, o enlace entre roteadores, os dispositivos existentes e os novos. Distinguir o que está no enunciado do que foi configurado no Lab 01 e das escolhas ainda abertas. | Inventário textual em [notas](notes.md), com as três redes identificadas. Nenhum desenho ou configuração nova é necessário. |
| 2. Planejar endereços | Investigar `/24`, `/30`, gateway e endereço estático. Reservar endereços para interfaces e servidores; planejar o pool DHCP da filial sem sobreposição. | Tabela de endereçamento preenchida e explicação de quais endereços podem ser usados no enlace `/30`. |
| 3. Montar a LAN de Sacramento | Ligar os quatro departamentos e configurar o servidor DHCP local. Prever quais opções cada PC deve receber e testar a comunicação local. | Amostras de DHCP e `ping` dentro da filial; configuração conferida em PCs de todos os departamentos. A comunicação com Uberaba ainda pode falhar. |
| 4. Ligar os roteadores | Escolher interfaces disponíveis no Packet Tracer, conectar os roteadores, configurar as interfaces das LANs e do enlace e verificar o estado delas. | Roteadores alcançam um ao outro pelo enlace; você explica o papel de cada interface. O enunciado não determina se o meio será Ethernet ou serial. |
| 5. Criar o caminho entre LANs | Investigar tabela de rotas e gateway padrão. Configurar ida e volta entre `192.168.1.0/24` e `192.168.2.0/24`, incluindo o retorno dos servidores de Uberaba e os gateways distribuídos por DHCP. | `ping` por IP da filial até os servidores da matriz e teste de retorno; rotas e gateways conferidos quando houver falha. |
| 6. Validar DNS e Web | Confirmar que o DHCP da filial entrega o endereço do DNS da matriz. Testar resolução de nome antes de abrir HTTP/HTTPS; separar falha de IP, DNS e aplicação. | Nome resolve para o Web correto e a página abre da filial; resultados registrados por departamento. |
| 7. Explicar e entregar | Revisar testes de todos os departamentos, salvar o `.pkt` e descrever o trajeto de uma consulta DNS e de uma requisição Web, inclusive a resposta. | Matriz de evidências completa, topologia salva e explicação própria do caminho dos pacotes. |

Os Labs [03: Ethernet e ARP](../03-ethernet-arp/assignment.md) e [04: sub-redes IPv4](../04-ipv4-subnets/assignment.md) são exercícios de apoio se ARP, máscara ou sub-rede dificultarem alguma etapa. O projeto WAN pode começar antes de concluí-los; a teoria necessária entra no momento em que for usada.

## Como começar a Etapa 1

Sem alterar o Packet Tracer ainda, confira o inventário textual das [notas](notes.md) e identifique o que já está no arquivo do Lab 01 e o que será acrescentado. Registre os endereços e as configurações que conseguir confirmar no `.pkt`; mantenha os demais como pendentes. No chat, explique em palavras as três redes e os serviços envolvidos. O mentor deve revisar suas observações e hipóteses antes de orientar a Etapa 2.

**English practice:** *branch office* = filial; *headquarters* = matriz; *WAN link* = enlace entre cidades; *default gateway* = porta de saída da sub-rede. Tente formular uma frase curta: “The branch office uses ...”.
