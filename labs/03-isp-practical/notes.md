# Notas e evidências — ISP

## Estado do trabalho

Topologia em [ISP Practical.pkt](ISP%20Practical.pkt). Os resultados abaixo foram relatados pelo estudante durante a montagem no Packet Tracer; as capturas compartilhadas na conversa mostram os equipamentos, os enlaces e parte dos pings, mas não substituem uma inspeção completa do `.pkt`.

- LANs locais montadas: ISP Conect, Show de Cacau matriz e filial, Açaí Kids, Mc Donuts matriz e duas filiais.
- Enlaces e rotas entre matriz e filial Show, e entre matriz Mc e suas duas filiais, testados.
- ISP interligado a Show, Açaí e Mc. Pings por IP entre o ISP e os clientes e entre as empresas relatados como funcionais.
- DNS no ISP configurado para os quatro sites; DHCP dos clientes atualizado para usar o DNS do ISP. Acesso aos sites por nome entre empresas relatado como funcional. Páginas HTML personalizadas adicionadas aos servidores.
- Após instalar outro módulo no roteador ISP sem antes salvar na NVRAM, os IPs seriais e as rotas estáticas desapareceram. O estudante identificou a falha por ping, `show ip interface brief` e `show ip route`, restaurou as portas e rotas e relatou que os testes voltaram a funcionar. Conferir o salvamento final na NVRAM.

## Decisão de endereçamento divergente do PDF

O PDF atribui `192.168.10.0/24` tanto à Açaí Kids quanto à matriz Mc Donuts. O estudante decidiu manter esse bloco na Mc Donuts e **alterar somente a Açaí Kids para `192.168.11.0/24`**, para que o ISP possa distinguir as duas redes por roteamento comum. Essa alteração deve ser explicada ao professor na entrega; não é um endereço fornecido pelo PDF. Os enlaces Mc Donuts `192.168.30.0/24` e `192.168.50.0/24` permaneceram com máscara `/24`, conforme o PDF.

## Endereçamento usado na sessão

Os endereços de rede vêm do PDF, exceto a LAN renumerada da Açaí. Os IPs individuais, início dos pools DHCP e domínios foram escolhidos para esta implementação. Os nomes exatos das interfaces físicas dos roteadores ainda precisam ser transcritos do Packet Tracer.

| Local | Rede LAN | Gateway | Servidor | DHCP a partir de | DNS entregue ao PC |
|---|---|---|---|---|---|
| ISP Conect | `172.16.1.0/24` | `172.16.1.1` | `172.16.1.2` | `172.16.1.100` | `172.16.1.2` |
| Show matriz | `192.168.1.0/24` | `192.168.1.1` | `192.168.1.2` | `192.168.1.100` | `172.16.1.2` |
| Show filial | `192.168.2.0/24` | `192.168.2.1` | `192.168.2.2` | `192.168.2.100` | `172.16.1.2` |
| Açaí Kids | `192.168.11.0/24` | `192.168.11.1` | `192.168.11.2` | Início do pool a conferir; PC recebeu `192.168.11.3` | `172.16.1.2` |
| Mc matriz | `192.168.10.0/24` | `192.168.10.1` | `192.168.10.2` | `192.168.10.100` | `172.16.1.2` |
| Mc Filial 01 | `192.168.20.0/24` | `192.168.20.1` | `192.168.20.2` | `192.168.20.100` | `172.16.1.2` |
| Mc Filial 02 | `192.168.40.0/24` | `192.168.40.1` | `192.168.40.2` | `192.168.40.100` | `172.16.1.2` |

| Enlace | Rede | Lado da matriz/ISP | Lado do cliente/filial | Estado |
|---|---|---|---|---|
| Show matriz ↔ filial | `192.168.3.0/30` | Matriz `192.168.3.1` | Filial `192.168.3.2` | Testado |
| Mc matriz ↔ Filial 01 | `192.168.30.0/24` | Matriz `192.168.30.1` | Filial `192.168.30.2` | Testado |
| Mc matriz ↔ Filial 02 | `192.168.50.0/24` | Matriz `192.168.50.1` | Filial `192.168.50.2` | Testado |
| ISP ↔ Show matriz | `172.16.2.0/30` | ISP `172.16.2.1` | Show `172.16.2.2` | Testado |
| ISP ↔ Açaí Kids | `172.16.3.0/30` | ISP `172.16.3.1` | Açaí `172.16.3.2` | Testado |
| ISP ↔ Mc matriz | `172.16.4.0/30` | ISP `172.16.4.1` | Mc `172.16.4.2` | Testado |

## Serviços e testes relatados

| Serviço ou caminho | Resultado relatado |
|---|---|
| DHCP, ping ao gateway e ao servidor, e acesso ao site por nome dentro de cada LAN | Funcionaram; Açaí foi testada novamente após a renumeração. |
| Show filial → servidor da matriz `192.168.1.2` e site `www.showdecacau.com` | Funcionaram. Uma captura mostrou o primeiro pacote de dois pings remotos expirar e os três seguintes responderem. |
| Filiais Mc → servidor da matriz `192.168.10.2` e site `www.mcdonuts.com` | Funcionaram. |
| ISP ↔ Show e ISP ↔ Mc, incluindo suas filiais | Pings por IP funcionaram nos dois sentidos, segundo relato. |
| Show ↔ Mc através do ISP | Pings por IP funcionaram, segundo relato. |
| Sites do ISP, Show e Mc por nome entre empresas | Funcionaram após registros DNS no ISP, atualização dos pools DHCP e renovação dos PCs, segundo relato. |
| Açaí ↔ ISP e Mc | Pings por IP funcionaram nos dois sentidos testados, segundo relato. |
| Açaí → sites do ISP, Show e Mc; Show e Mc → site da Açaí | Páginas abriram por nome após a integração ao DNS do ISP, segundo relato. |

Registros DNS no ISP: `www.ispconect.com` → `172.16.1.2`, `www.showdecacau.com` → `192.168.1.2`, `www.mcdonuts.com` → `192.168.10.2`, `www.acaikids.com` → `192.168.11.2`.

## Evidências da revisão final

Capturas do estudante de 18/11/2026 mostram:

- No ISP, `show ip route` lista como conectadas as redes `172.16.1.0/24`, `172.16.2.0/30`, `172.16.3.0/30` e `172.16.4.0/30`. Há rotas estáticas para `192.168.1.0/24`, `192.168.2.0/24`, `192.168.10.0/24`, `192.168.11.0/24`, `192.168.20.0/24` e `192.168.40.0/24`, com próximos saltos dos clientes correspondentes.
- No roteador Açaí, `show ip route` lista `172.16.3.0/30` e `192.168.11.0/24` como conectadas e `S* 0.0.0.0/0 via 172.16.3.1` como rota padrão.
- No PC da Açaí, `ipconfig /all` mostra `192.168.11.3/24`, gateway `192.168.11.1`, DHCP `192.168.11.2` e DNS `172.16.1.2`. O IP `.3` é válido nessa LAN, mas difere do início `.100` planejado; conferir o pool se for necessário reproduzir exatamente o plano.

## Fechamento e revisão

O estudante confirmou que salvou os roteadores na NVRAM e a versão final do `.pkt`. Os testes funcionais por IP e por nome foram relatados como concluídos. O arquivo do Packet Tracer foi salvo após a integração da Açaí.

Para a revisão da prova: conferir IP, máscara, gateway e DNS de um PC; ler `show ip route` no ISP e em um cliente; explicar o caminho de uma consulta DNS e de uma requisição Web entre empresas, incluindo as respostas. Na entrega, informar a decisão de renumerar a Açaí e, se necessário, transcrever os nomes das interfaces físicas do `.pkt` para esta tabela.
