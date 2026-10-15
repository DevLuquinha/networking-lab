# Estudos de Redes

Plano prático de Redes para quem desenvolve backend e quer construir fundamentos úteis em Linux, infraestrutura, cloud e cybersecurity. O estudo parte de uma [LAN já montada no Cisco Packet Tracer](labs/01-company-lan/assignment.md) e avança por experimentos menores, análise de tráfego e diagnóstico.

Este repositório guarda o plano e as evidências de aprendizado. Não há agenda por dias: o avanço depende de conseguir explicar, observar e diagnosticar cada assunto.

## Por onde começar

1. Leia o [roadmap](docs/roadmap.md) para entender a ordem e os critérios de avanço.
2. Escolha no [método de estudo](docs/study-method.md) se quer começar o módulo com pesquisa guiada ou seguir para a explicação e o laboratório.
3. Revise o [Lab 01](labs/01-company-lan/assignment.md) como ponto de partida. Depois, faça o [Lab 02: Ethernet e ARP](labs/02-ethernet-arp/assignment.md) e o [Lab 03: sub-redes IPv4](labs/03-ipv4-subnets/assignment.md).
4. Registre descobertas, dúvidas e evidências em [progresso](docs/progress.md). O registro representa o que você confirmou.

## Como os labs funcionam

Cada enunciado apresenta uma pergunta de rede, uma experiência e formas de observar o resultado. Primeiro faça uma previsão; depois monte, teste e explique o que ocorreu. Leve ao chat sintomas, saídas de comandos, capturas ou eventos do Packet Tracer quando precisar de ajuda. O assistente ajuda a investigar antes de propor uma correção completa.

Os termos técnicos em inglês aparecem junto às explicações em português. A leitura e as respostas em inglês aumentam gradualmente, conforme descrito no [método](docs/study-method.md).

## Ferramentas

Cisco Packet Tracer, Linux, Wireshark, Docker, `tcpdump`, `curl`, `ping`, `traceroute`, `dig`/`nslookup`, `ip` e `ss`. Cada módulo usa as ferramentas necessárias para responder às perguntas daquele momento.
