# Lab 03 — IPv4, máscara e sub-redes

## Pergunta do laboratório

Como um host decide se o IPv4 de destino está na sua sub-rede? O que acontece quando dois grupos têm endereços de sub-redes diferentes, mas estão ligados ao mesmo switch e ainda não existe roteador?

Este lab aprofunda a rede `/24` usada no [Lab 01](../01-company-lan/assignment.md). Antes da prática, você pode escolher a [pesquisa guiada](../../docs/study-method.md) sobre CIDR, endereço de rede, broadcast e gateway.

## Planejamento antes da topologia

Use `192.168.20.0/24` como bloco disponível. Divida-o em sub-redes `/26` e escolha **duas sub-redes diferentes** para os grupos A e B. Para cada uma, anote:

- endereço de rede e máscara em decimal;
- primeiro e último endereço utilizável por hosts;
- endereço de broadcast;
- dois endereços de host que você pretende configurar.

Mostre o cálculo ou a regra que usou. Confira se não reservou endereço de rede ou broadcast para um PC.

## Montagem e previsões

- No Packet Tracer, ligue quatro PCs a um mesmo switch: A1 e A2 na primeira sub-rede; B1 e B2 na segunda.
- Configure endereços estáticos e a máscara `/26` que planejou. Deixe o gateway vazio; este lab ainda não adiciona um roteador.
- Antes dos testes, preveja o resultado de `ping` entre A1 e A2, entre B1 e B2 e entre A1 e B1. Explique sua previsão com base na máscara e na ausência de rota para outra sub-rede.

Estar no mesmo switch não significa, por si só, estar na mesma sub-rede IPv4. Observe como essa diferença aparece no teste.

## Testes e investigação

1. Execute os três `ping` previstos e registre a configuração e o resultado exato de cada um. Um destino sem rota pode aparecer como timeout ou mensagem de destino inalcançável, conforme o ambiente; investigue o caminho em vez de depender da frase exibida.
2. Use o modo Simulation para acompanhar ARP e ICMP em pelo menos um teste que funciona e um que falha. A ausência de um pacote também é uma observação: registre-a se o host interromper o envio por não ter uma rota. Explique qual próximo salto o host tenta encontrar, ou por que não consegue prosseguir.
3. Escolha um PC e altere somente sua máscara para uma máscara incorreta. Antes de repetir os testes, preveja o efeito. Registre o que ocorreu e restaure a configuração original.

## Desafio de planejamento

Sem montar outra topologia, proponha uma divisão de `192.168.30.0/24` para três grupos que precisam de **50, 20 e 10 hosts**, respectivamente. Use VLSM e apresente rede, prefixo, intervalo utilizável e broadcast de cada grupo. Verifique que não há sobreposição. Se ainda não estudou VLSM, registre este desafio como próximo passo do módulo.

## Evidências e conclusão

Guarde sua tabela de endereçamento, as previsões, os resultados e uma explicação da decisão que o host fez para cada destino. O lab termina quando você consegue identificar a sub-rede de qualquer endereço configurado, justificar os `ping` observados e explicar o que falta para que os dois grupos se comuniquem. O projeto e diagnóstico da comunicação entre sub-redes serão aprofundados no módulo de roteamento do [roadmap](../../docs/roadmap.md).

Registre no [progresso](../../docs/progress.md) quais cálculos já faz sem ajuda e quais ainda precisam de revisão.

## Inglês técnico

Termos: *subnet* (sub-rede), *subnet mask* (máscara), *prefix length* (comprimento do prefixo), *network address*, *broadcast address*, *host range* e *default gateway*.

Responda com uma ou duas frases, em inglês ou misturando os idiomas: **“Why can A1 reach A2 but not B1?”** Priorize a explicação da rede; o mentor ajuda com o inglês depois.
