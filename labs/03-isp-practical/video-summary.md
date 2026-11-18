# Resumo da videoaula do ISP

Fonte: [Prática de Redes — Criação e configuração de um ISP](https://www.youtube.com/watch?v=VdqleBOIbRE), transcrição automática em português. Os tempos são aproximados. A aula demonstra um exemplo diferente do enunciado deste lab.

| Trecho | O que o professor faz e ensina |
|---|---|
| 0:14–5:49 | Apresenta três empresas e um ISP. Organiza locais no ambiente físico do Packet Tracer, nomeando matriz e filial de cada cliente. Propõe construir primeiro as LANs e depois as interligações. |
| 5:49–14:47 | Monta a LAN do ISP com switch, PC, roteador e um servidor que reúne HTTP, DHCP e DNS. Define IP fixo para servidor e gateway, pool DHCP para o PC, registro DNS para o site e testa o acesso. |
| 15:06–28:43 | Monta a primeira empresa com matriz e filial, servidores e PCs. Configura DHCP local, Web na matriz e DNS; na filial aponta o DNS para a matriz. |
| 28:43–43:03 | Adiciona portas seriais aos roteadores com o equipamento desligado, liga matriz e filial, usa um `/30` no enlace e cria rotas estáticas nos dois sentidos. Insiste em salvar a configuração antes de desligar o roteador e diagnostica com pings sucessivos. |
| 49:27–1:02:09 | Repete a estrutura de LAN, serviços, enlace e rotas para a segunda empresa. |
| 1:02:09–1:12:05 | Liga as matrizes das empresas ao ISP por enlaces distintos, cada um com sua própria rede. Configura rotas para as LANs dos clientes e rotas de retorno. Testa primeiro por IP. |
| 1:12:05–1:25:21 | Centraliza os registros DNS dos sites no servidor do ISP. Altera o DNS entregue por DHCP e renova a configuração dos PCs. Mostra que alcançar o Web por IP e abrir por nome são testes diferentes. |
| 1:25:21–1:43:22 | Repete a ligação para outro cliente, ajusta rotas entre clientes e acessa páginas do ISP e das empresas por nome. Uma terceira empresa é deixada como exercício ao estudante. |

## Método de diagnóstico extraído da aula

1. Verificar IP, máscara, gateway e interface ativa.
2. Testar o próximo salto por IP e avançar salto a salto.
3. Conferir rotas de ida **e** retorno em cada roteador (`show ip route`).
4. Testar o servidor Web por IP.
5. Conferir qual DNS o cliente recebeu e se ele conhece o domínio.
6. Renovar DHCP nos clientes após alterar gateway ou DNS no pool.
7. Testar pelo nome no navegador.

**Nota técnica:** em rota estática, o próximo salto deve ser o IP da interface do roteador vizinho (por exemplo, `.1` ou `.2` do enlace `/30`), e não o endereço da rede (`.0`). A transcrição automática registra várias falas como se o professor tivesse inserido `.0`; não usar isso como receita sem conferir a tela e a tabela de rotas.
