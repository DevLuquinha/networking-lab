# Roadmap técnico de Redes

## Objetivo e ponto de partida

Construir fundamentos de Redes aplicáveis a backend, Linux, infraestrutura, cloud e cybersecurity. O [Lab 01](../labs/01-company-lan/assignment.md) já reúne switches departamentais em uma LAN `192.168.1.0/24`, DHCP, DNS e Web. Ele é a referência inicial: ao avançar, volte a ele para explicar com mais precisão o caminho de um pacote e a origem de possíveis falhas.

Os módulos seguem dependências conceituais, sem duração fixa. A sessão opcional de [pesquisa guiada](study-method.md) pode anteceder qualquer lab. Packet Tracer, Linux, Wireshark e `tcpdump` são usados ao longo do percurso; o módulo de diagnóstico em Linux consolida essas práticas antes de Docker.

**Profundidade:** *observar* = reconhecer e explicar um comportamento; *operar* = configurar, testar e diagnosticar; *projetar* = escolher uma solução, justificar e verificar seus limites. Um módulo está concluído quando você consegue produzir as evidências descritas, sem depender de uma resposta decorada.

| Ordem | Assunto e dependência | Profundidade e objetivo observável | Lab previsto e critério de avanço |
|---|---|---|---|
| 0 | Revisão da LAN existente | Observar: descrever hosts, switches, endereços, serviços e testes já feitos. | [Lab 01](../labs/01-company-lan/assignment.md): mapear o que já funciona e registrar perguntas ainda sem resposta. |
| 1 | Ethernet, MAC, switch, broadcast e ARP | Operar: prever e reconhecer quadros de broadcast e unicast e explicar como o switch aprende endereços. | [Lab 02](../labs/02-ethernet-arp/assignment.md): observar ARP e ICMP no Packet Tracer; explicar a sequência de eventos. |
| 2 | IPv4, CIDR, sub-redes e ICMP; depende de 1 | Projetar: calcular rede, broadcast, intervalo de hosts e máscara; distinguir mesma sub-rede de outra. | [Lab 03](../labs/03-ipv4-subnets/assignment.md): endereçar duas sub-redes e justificar os resultados dos `ping`; estender o plano com VLSM. |
| 3 | Gateway, tabelas de rota, roteamento estático, VLANs e NAT; depende de 2 | Projetar: conectar e diagnosticar uma rede pequena com várias sub-redes; explicar o próximo salto e quando ocorre tradução de endereço. Protocolos dinâmicos, como OSPF e BGP, ficam em nível conceitual nesta etapa. | Lab futuro: interligar sub-redes e VLANs; validar com rotas, `ping` e `traceroute`, incluindo uma falha de gateway ou rota. |
| 4 | TCP, UDP, portas, sockets e noções de MTU; depende de 3 | Operar: relacionar processo, endereço e porta; reconhecer estabelecimento e encerramento de uma conexão TCP e diferenças práticas de UDP. | Lab futuro: inspecionar conexões com `ss`, `curl` e captura de pacotes; explicar uma falha de porta ou serviço. |
| 5 | DHCP, DNS, HTTP e TLS; depende de 2 e 4 | Operar: seguir a configuração do host, a resolução de nome e a requisição Web; localizar a etapa que falhou. | Lab futuro: revisitar os serviços do Lab 01 e comparar `dig`/`nslookup`, `curl` e capturas; explicar DNS, HTTP e HTTPS separadamente. |
| 6 | Diagnóstico em Linux e análise de pacotes; consolida 1–5 | Operar: inspecionar interfaces, vizinhos, endereços, rotas, DNS, sockets e tráfego com `ip`, `ss`, `tcpdump` e Wireshark. | Lab futuro: diagnosticar uma configuração quebrada a partir de sintomas e evidências, registrar hipótese, teste e causa. |
| 7 | Redes Docker e backend; depende de 6 | Projetar: explicar bridge, DNS entre containers, portas publicadas, isolamento e o caminho cliente → host → serviço. | Lab futuro: conectar serviços em redes Docker, expor uma API e explicar acessos que funcionam ou falham com `curl`. |
| 8 | IPv6; depende de 2 e 3 | Operar: reconhecer endereços, prefixos, gateway e descoberta de vizinhos; comparar o encaminhamento essencial com IPv4. | Lab futuro: configurar e observar comunicação IPv6 em topologia pequena ou namespaces Linux. |
| 9 | Segmentação e segurança; depende de 3, 5 e 6 | Projetar: aplicar VLANs, ACLs/firewall, zonas de confiança e TLS; verificar fluxos permitidos e bloqueados. | Lab futuro: restringir acesso entre redes e serviços, registrar a política esperada e demonstrar cada resultado. |
| 10 | Redes em cloud; depende de 3, 7 e 9 | Projetar: relacionar VPC/VNet, sub-redes, tabelas de rota, NAT, regras de acesso, balanceamento, DNS e VPN aos fundamentos. | Lab futuro: desenhar uma arquitetura pequena e justificar caminhos e controles; conta paga em cloud não é requisito. |

## Aprofundamentos depois da base

- **Cybersecurity:** ampliar análise de tráfego, segmentação, regras de firewall, detecção e investigação em ambientes próprios e autorizados.
- **Engenharia de IA:** estudar latência, timeouts, retries, proxies, balanceamento, comunicação entre serviços, observabilidade e redes de infraestrutura distribuída.
- **Tópicos de reconhecimento:** Wi-Fi e protocolos de roteamento dinâmico podem ser explorados com mais profundidade quando um projeto ou objetivo concreto exigir.

O [registro de progresso](progress.md) mostra o que foi comprovado em cada etapa. Avance quando conseguir explicar *por que* o resultado ocorreu e como investigaria uma falha semelhante.
