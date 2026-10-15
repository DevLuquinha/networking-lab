# Lab 02 — Ethernet, switch e ARP

## Pergunta do laboratório

Como um PC envia tráfego para outro PC da mesma LAN quando conhece o endereço IPv4 de destino, mas ainda não conhece seu endereço MAC? O que o switch faz com cada quadro?

Este lab separa uma parte do [Lab 01](../01-company-lan/assignment.md) para observá-la com atenção. Você pode começar com a [pesquisa guiada](../../docs/study-method.md) antes de montar a topologia.

## Preparação

- Ferramenta principal: Cisco Packet Tracer, no modo **Simulation**.
- Topologia: um switch Ethernet e três PCs (A, B e C), todos ligados ao switch.
- Configure os três PCs com endereços distintos da mesma rede `192.168.10.0/24`. Não configure gateway nem serviços; eles não são necessários para a comunicação entre esses hosts.
- Registre os endereços IPv4 e MAC escolhidos. Use uma topologia nova ou confirme que a simulação começa sem entradas aprendidas que escondam a descoberta inicial.

Não há arquivo `.pkt` pronto: a montagem faz parte da tentativa.

## Previsões antes de executar

1. A conhece o IPv4 de B. Qual informação ainda precisa para enviar um quadro Ethernet diretamente a B?
2. Qual mensagem você espera que A envie primeiro? Quem deve recebê-la: apenas B ou também C?
3. Depois que B responder, quais endereços devem aparecer no quadro que transporta o `ping`?

Escreva suas hipóteses antes de iniciar a simulação. Se não souber alguma resposta, registre a dúvida.

## Experimento

1. No modo Simulation, filtre ou acompanhe eventos **ARP** e **ICMP**.
2. Execute `ping` de A para B. Avance evento por evento e anote origem, destino, protocolo e portas do switch envolvidas. Se a primeira tentativa de `ping` não responder, acompanhe a sequência completa antes de concluir que a rede falhou.
3. Repita o `ping` de A para B e compare a sequência com a primeira tentativa.
4. Execute `ping` de C para B. Observe se o caminho de descoberta é igual ao de A.
5. Consulte a tabela MAC do switch, se disponível no modelo usado, e compare os endereços aprendidos com os quadros observados. Em switches Cisco do Packet Tracer, `show mac address-table` costuma mostrar essa tabela.

## Investigue uma falha

Escolha **uma** alteração, como desconectar um enlace ou configurar um host em outra sub-rede. Antes de alterar, preveja o resultado. Depois, registre o que apareceu na simulação e formule uma hipótese para explicar a diferença. Volte à configuração original ao encerrar.

## Evidências e conclusão

Registre uma tabela curta com pelo menos: evento, MAC de origem, MAC de destino, quem recebeu e por que. Explique com suas palavras:

- quais quadros foram enviados a todos os hosts da LAN e quais foram dirigidos a um host;
- como o switch aprendeu por qual porta alcançar cada MAC;
- por que a segunda comunicação pode mostrar menos eventos de descoberta;
- em que ponto sua previsão estava certa ou precisou ser corrigida.

O lab termina quando você consegue reconstruir a sequência ARP → comunicação IP/ICMP a partir dos eventos, incluindo o comportamento observado na falha que criou. Registre dúvidas no [progresso](../../docs/progress.md).

### Observação opcional em Linux

Se tiver um ambiente Linux de laboratório, compare a descoberta de vizinhos com `ip neigh` e uma captura ARP/ICMP no Wireshark ou `tcpdump`. Anote o que de fato observou e quais detalhes diferem da simulação do Packet Tracer. Esta extensão não é requisito para concluir o lab.

## Inglês técnico

Termos: *frame* (quadro), *MAC address* (endereço MAC), *broadcast*, *unicast*, *switch port* (porta do switch), *ARP request* e *ARP reply*.

Responda com uma ou duas frases, em inglês ou misturando os idiomas: **“Why does the ARP request reach PC C?”** O mentor pode ajudar a ajustar a frase depois de discutir sua explicação técnica.
