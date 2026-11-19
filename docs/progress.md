# Progresso de aprendizagem

Este registro pertence ao estudante. Use **não iniciado**, **em estudo**, **aplicado** ou **explicado e diagnosticado** para descrever o estágio observado. Uma execução bem-sucedida não comprova, sozinha, que você consegue explicar ou diagnosticar o assunto. Atualize a tabela somente após revisar as evidências.

| Módulo | Estado | Evidência ou explicação sua | Dúvida / próximo passo |
|---|---|---|---|
| 0. LAN inicial | Aplicado anteriormente | [Topologia no Packet Tracer](../labs/01-company-lan/coisa-qualquer.pkt); enunciado em [Lab 01](../labs/01-company-lan/assignment.md). | Revisitar os fluxos internos ao estudar cada camada. |
| Projeto WAN Uberaba–Sacramento | Aplicado | [Lab 02 no Packet Tracer](../labs/02-company-wan/coisa-qualquer-wan.pkt) e [evidências](../labs/02-company-wan/notes.md): DHCP na filial, enlace serial, rotas, pings entre LANs, DNS e HTTP. HTTPS funcionou segundo relato do estudante. | Revisitar o caminho completo da requisição e resposta Web e observar HTTPS/TLS em uma sessão futura. |
| Projeto ISP preparatório | Aplicado | [Topologia](<../labs/03-isp-practical/ISP Practical.pkt>) e [notas](../labs/03-isp-practical/notes.md): sete LANs, três enlaces cliente–ISP, WANs das filiais, DHCP, DNS central e sites por nome. Pings e páginas funcionaram segundo relato; capturas confirmam rotas do ISP e da Açaí e IP/gateway/DNS do PC da Açaí. Perda de IPs seriais e rotas após reinício foi diagnosticada e corrigida. | Revisar a explicação completa de DNS → HTTP e das respostas sem consultar; informar ao professor a mudança da Açaí para `192.168.11.0/24`. |
| 1. Ethernet e ARP | Não iniciado | — | [Lab 04](../labs/04-ethernet-arp/assignment.md), quando for útil ao projeto. |
| 2. IPv4 e sub-redes | Não iniciado | — | [Lab 05](../labs/05-ipv4-subnets/assignment.md), quando for útil ao projeto. |
| 3. Gateway, roteamento, VLANs e NAT | Em estudo | Gateway, rotas estáticas e rota padrão aplicados no Lab 03; tabela de rotas usada para diagnosticar o ISP após reinício. | Explicar o próximo salto e o caminho de ida e retorno sem consultar; estudar VLANs e NAT depois. |
| 4. TCP, UDP e portas | Não iniciado | — | — |
| 5. DHCP, DNS, HTTP e TLS | Em estudo | DHCP, DNS e HTTP configurados e testados no Lab 03; IP, gateway e DNS conferidos no PC da Açaí. | Aprofundar as mensagens DHCP, a consulta DNS, a requisição HTTP e TLS; não inferir domínio desses protocolos a partir da página aberta. |
| 6. Diagnóstico em Linux | Não iniciado | — | — |
| 7. Redes Docker e backend | Não iniciado | — | — |
| 8. IPv6 | Não iniciado | — | — |
| 9. Segmentação e segurança | Não iniciado | — | — |
| 10. Redes em cloud | Não iniciado | — | — |

## Resumo de continuidade entre sessões

Use estes campos quando um chat ficar longo ou ao abrir uma nova conversa. Guarde só o que ajuda a próxima investigação.

- **Módulo e objetivo:** Lab 03 ISP aplicado; preparar a explicação do caminho PC → DNS → servidor Web e das respostas.
- **O que consigo explicar sem consultar:** a compreensão de rotas estáticas e próximo salto foi afirmada pelo estudante após a explicação; uma explicação completa feita por ele ainda não foi registrada.
- **Evidência observada (arquivo, captura ou comando e saída):** [topologia](<../labs/03-isp-practical/ISP Practical.pkt>), [notas](../labs/03-isp-practical/notes.md), `show ip route` no ISP e na Açaí, `ipconfig /all` do PC Açaí com `192.168.11.100/24`, gateway `192.168.11.1` e DNS `172.16.1.2`; testes de ping e sites relatados como funcionais.
- **Minha hipótese ou dúvida aberta:** nenhuma falha funcional relatada; explicar ao professor a sobreposição do PDF e a renumeração da Açaí.
- **Próximo experimento:** após a revisão para a prova, [Lab 04 — Ethernet e ARP](../labs/04-ethernet-arp/assignment.md), seguido do [Lab 05 — sub-redes IPv4](../labs/05-ipv4-subnets/assignment.md).
- **Termos em inglês praticados:** default gateway, static route, next hop, DHCP, DNS, HTTP, running configuration e startup configuration.
- **Preferência de condução nesta fase:** explicações diretas em português, blocos curtos de configuração e reforço do que foi configurado e testado; o estudante pediu para dispensar previsões por falta de tempo.
