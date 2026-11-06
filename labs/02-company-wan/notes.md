# Notas do Lab 02 — preencher durante a atividade

Este arquivo é um espaço para suas previsões e evidências. Deixe campos vazios até investigá-los; o mentor não deve marcar uma etapa como concluída por você.

## Etapa 1 — ponto de partida e inventário

O enunciado do Lab 01 prevê, na matriz, cinco switches departamentais, 12 PCs, um servidor DNS/DHCP e um servidor Web na rede `192.168.1.0/24`. O enunciado deste lab prevê, na filial, quatro switches, 17 PCs, um servidor DHCP e a rede `192.168.2.0/24`; o enlace entre os roteadores usa `10.1.1.0/30`. Estes são requisitos dos enunciados, ainda não uma descrição verificada dos arquivos `.pkt`.

### Observações nas capturas do Packet Tracer enviadas pelo estudante

- A topologia mostra cinco switches departamentais (DTI, Fiscal, RH, Vendas e Produção), 12 PCs e dois servidores. O switch do DTI interliga os demais switches. Não há roteador visível.
- O servidor DNS/DHCP usa `192.168.1.2/24`, DNS `192.168.1.2` e gateway IPv4 `0.0.0.0`.
- O serviço DHCP está ligado. O pool `serverPool` começa em `192.168.1.100`, usa máscara `255.255.255.0`, DNS `192.168.1.2`, gateway `0.0.0.0` e limite de 100 usuários.
- O serviço DNS está ligado e contém um registro A: `www.coisaqualquer.com.br` → `192.168.1.3`.
- O servidor Web usa `192.168.1.3/24`, DNS `192.168.1.2` e gateway IPv4 `0.0.0.0`. As capturas ainda não mostram o estado dos serviços HTTP e HTTPS.
- O `PC-FISCAL-02` recebeu `192.168.1.106/24`, servidor DHCP `192.168.1.2`, DNS `192.168.1.2` e gateway IPv4 `0.0.0.0`. Isso confirma um cliente, não todos os PCs.

**A conferir na continuação:** se o arquivo `.pkt` aberto corresponde à versão final do Lab 01; estado de HTTP/HTTPS; configuração de outros PCs, se houver divergência; escolha do futuro gateway da matriz. Nenhuma mudança foi feita no Lab 01 nesta etapa.

- **Minha previsão sobre a comunicação com outra sub-rede:** sem gateway IPv4 configurado, o PC da matriz não consegue enviar tráfego à rede da filial. Os servidores da matriz também precisarão de um caminho de retorno para responder a clientes de outra sub-rede. O valor `0.0.0.0` indica ausência de gateway, não um gateway local.
- **O que precisarei acrescentar à matriz e à filial:**
- **Dúvidas sobre os enunciados:**

## Etapa 2 — plano de endereçamento

Esta tabela distingue o plano do que já foi observado. O gateway `192.168.1.4` foi escolhido e testado na matriz; `192.168.2.4` segue o mesmo padrão na filial.

| Rede / dispositivo | Endereço e máscara escolhidos | Por que escolhi | Conferido no Packet Tracer? |
|---|---|---|---|
| LAN de Uberaba | `192.168.1.0/24` | Rede já usada no Lab 01 | Sim, nas capturas |
| DNS/DHCP da matriz | `192.168.1.2/24` | Servidor fixo existente; gateway `192.168.1.4` | IP e gateway confirmados em capturas |
| Web da matriz | `192.168.1.3/24` | Servidor fixo existente; gateway `192.168.1.4` | IP e gateway confirmados em capturas |
| Interface LAN do roteador de Uberaba | `192.168.1.4/24` | Gateway escolhido fora do pool DHCP | Configuração e ping local relatados pelo estudante; pings entre LANs confirmam o encaminhamento |
| PCs da matriz | DHCP: pool a partir de `192.168.1.100/24`, até 100 clientes | Distribuição automática; gateway `192.168.1.4` | Pool atualizado confirmado em captura; um PC renovado alcançou a filial |
| Interface WAN do roteador de Uberaba | `10.1.1.1/30` | Primeiro endereço utilizável do enlace | Configuração e ping do enlace confirmados em capturas |
| Interface WAN do roteador de Sacramento | `10.1.1.2/30` | Segundo endereço utilizável do enlace | Ping a partir de Uberaba confirmou resposta da interface |
| LAN de Sacramento | `192.168.2.0/24` | Rede pedida no enunciado | A captura mostra os quatro switches, 17 PCs e o servidor DHCP conectados; ping de Vendas para Produção confirmado |
| Interface LAN do roteador de Sacramento | `192.168.2.4/24` | Gateway da filial, seguindo o padrão da matriz | Configuração e ping local relatados pelo estudante; pings entre LANs confirmam o encaminhamento |
| DHCP da filial | `192.168.2.2/24` | Servidor fixo fora do pool de clientes | IP e máscara mostrados em captura; gateway corrigido segundo relato do estudante |
| PCs da filial | DHCP: pool a partir de `192.168.2.100/24`, até 100 clientes | Endereços automáticos para os 17 PCs; gateway `192.168.2.4`, DNS `192.168.1.2` | Concessões confirmadas em capturas de um PC por departamento; estudante relata que os demais PCs também funcionaram |

No enlace `10.1.1.0/30`, `10.1.1.0` é o endereço da rede e `10.1.1.3` é o broadcast; por isso as interfaces recebem `.1` e `.2`. Os PCs não terão IP fixo por departamento: a ordem das concessões DHCP determinará o endereço de cada um.

**Rotas previstas:** Uberaba usa uma rota para `192.168.2.0/24` via `10.1.1.2`; Sacramento usa uma rota para `192.168.1.0/24` via `10.1.1.1`. As capturas mostram a rota estática de Uberaba e pings entre as LANs nos dois sentidos. A configuração da rota em Sacramento foi relatada pelo estudante.

## Etapas 3–6 — previsão, teste e diagnóstico

| Teste | Minha previsão | Resultado observado e evidência | Hipótese ou explicação |
|---|---|---|---|
| DHCP em cada departamento de Sacramento | O PC do DTI receberia IP sem roteador; a solicitação DHCP atravessaria os switches departamentais | Capturas: DTI `.100`, Administrativo `.101`, Produção `.109` e Vendas `.111`, todos em `192.168.2.0/24`; os PCs mostrados receberam gateway `192.168.2.4` e DNS `192.168.1.2`. O estudante relata que todos os 17 PCs funcionaram; as capturas documentam uma amostra por departamento. | O broadcast de DHCP alcança o servidor pelos switches interligados na mesma LAN; receber parâmetros de DNS e gateway não confirma que esses destinos já sejam alcançáveis. |
| Comunicação dentro da filial | O ping ao servidor DHCP `192.168.2.2` responderia; um PC de Vendas alcançaria o PC de Produção `192.168.2.109` sem roteador | Capturas de DTI, Administrativo, Produção e Vendas: 4 respostas de `192.168.2.2` e 0% de perda em cada teste. `PC-VENDAS-SACRAMENTO-06` recebeu 4 respostas de `192.168.2.109`, também com 0% de perda. | Os clientes e o servidor estão na mesma LAN `192.168.2.0/24`; o host descobre o MAC do destino local por ARP e envia o ICMP pela rede de switches, sem roteador. |
| Comunicação entre os roteadores | O enlace serial precisava de IPs e interfaces ativas | Ping de `R-UBERABA` para `10.1.1.2`: 5/5 respostas. A tabela de Uberaba mostra `S 192.168.2.0/24 via 10.1.1.2`. | O enlace `10.1.1.0/30` funciona e Uberaba tem rota estática para a LAN da filial. |
| PC da filial → DNS da matriz por IP | Antes de configurar os roteadores, o ping a `192.168.1.2` falharia | O estudante relatou que, após configurar rotas e gateway do servidor DNS/DHCP da matriz, o ping de Sacramento para `192.168.1.2` funcionou. | A configuração DHCP já entregava o IP do DNS; o acesso só passou a funcionar quando houve caminho entre as LANs e caminho de volta. |
| PC da filial → Web da matriz por IP | O acesso exigia rota e gateway no servidor Web | Captura do PC de Sacramento: ping a `192.168.1.3` com 4/4 respostas e 0% de perda. `R-UBERABA` também alcançou o servidor Web com 5/5 respostas. | O servidor Web está acessível por IP a partir da filial; isso ainda não confirma DNS, HTTP ou HTTPS. |
| PC da matriz → DHCP da filial por IP | PCs da matriz precisariam renovar o DHCP para receber o novo gateway `192.168.1.4` | Captura do `PC-DTI-02`: ping a `192.168.2.2` com 4/4 respostas e 0% de perda. O teste anterior falhou em um PC que ainda não tinha renovado a concessão DHCP. | Alterar o pool DHCP não atualiza imediatamente as configurações já recebidas pelos clientes; cada PC precisa renovar sua concessão. |
| Resolução do nome Web na filial | O DNS da matriz devolveria o IP do Web | Captura do `PC-ADM-SACRAMENTO-02`: `ping www.coisaqualquer.com.br` resolveu para `192.168.1.3` e recebeu 4/4 respostas. | O cliente da filial alcança o DNS da matriz; o nome aponta para o Web, e ICMP chega ao IP resolvido. |
| HTTP/HTTPS pelo nome na filial | A página da matriz abriria pelo domínio | Captura do navegador em Sacramento mostra `http://www.coisaqualquer.com.br` com a página da empresa. O estudante relata que HTTPS também funcionou, mas não enviou captura desse acesso. | O teste HTTP confirma acesso à aplicação pelo nome. A captura não comprova HTTPS separadamente. |

## Etapa 7 — explicação final

- **Explicação inicial do estudante:** o PC de Sacramento passa pelo switch do departamento, chega ao roteador da filial e ao roteador de Uberaba, que encaminha a consulta para o DNS no DTI. Na revisão, foi distinguido o switch do DTI de cada cidade dos dois roteadores e esclarecido que o DNS devolve o IP do servidor Web, não a página.
- **Caminho da consulta DNS e da resposta, após revisão:** o estudante descreveu o retorno como servidor DNS → switch do DTI de Uberaba → `R-UBERABA` → `R-SACRAMENTO` → switch do DTI de Sacramento → switch departamental → PC solicitante. O endereço devolvido é `192.168.1.3`.
- **Caminho da requisição Web e da resposta, após revisão:** foi esclarecido pelo mentor que, após receber `192.168.1.3` do DNS, o navegador ainda precisa estabelecer a conexão com o servidor Web, enviar a requisição HTTP e receber o conteúdo antes de renderizar a página; em HTTPS, há negociação TLS antes da requisição. O estudante ainda não reformulou esse trajeto completo com suas próprias palavras.
- **Erro que encontrei, hipótese que testei e causa confirmada:** um ping da matriz para Sacramento falhou em um PC que ainda mantinha a concessão DHCP antiga, sem o novo gateway. Após renovar o DHCP do PC, o ping respondeu 4/4.
- **A revisitar:** trajeto completo da resposta Web e detalhes de TCP/TLS em uma sessão posterior.

## Fechamento da sessão

- O estudante explicou por que `10.1.1.0/30` contém quatro endereços: 30 bits de rede deixam dois bits, então `2² = 4` combinações; `.0` é a rede, `.1` e `.2` são utilizáveis e `.3` é o broadcast. Também aplicou a regra a `/28`: quatro bits restantes produzem 16 endereços, de `.0` a `.15` no bloco `10.1.1.0/28`.
- O estudante encerrou o tópico por hoje. O estado no [registro de progresso](../../docs/progress.md) é **aplicado**, conforme as evidências; aprofundamento em Web/TLS pode ficar para o módulo correspondente.
