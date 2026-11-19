# Notas e evidências — ISP

## Estado do trabalho

Topologia em [ISP Practical.pkt](ISP%20Practical.pkt). Os resultados abaixo foram relatados pelo estudante durante a montagem no Packet Tracer; as capturas compartilhadas na conversa mostram os equipamentos, os enlaces e parte dos pings, mas não substituem uma inspeção completa do `.pkt`.

- LANs locais montadas: ISP Conect, Show de Cacau matriz e filial, Açaí Kids, Mc Donuts matriz e duas filiais.
- Enlaces e rotas entre matriz e filial Show, e entre matriz Mc e suas duas filiais, testados.
- ISP interligado a Show e Mc. Pings por IP entre essas redes e entre as duas empresas relatados como funcionais.
- DNS no ISP configurado para os sites do ISP, Show e Mc; DHCP desses clientes atualizado para usar o DNS do ISP. Acesso aos sites por nome entre empresas relatado como funcional. Páginas HTML personalizadas adicionadas aos servidores.
- Açaí Kids renumerada e testada **localmente**; seu enlace com o ISP, as rotas e o registro no DNS central ainda não foram configurados.

## Decisão de endereçamento divergente do PDF

O PDF atribui `192.168.10.0/24` tanto à Açaí Kids quanto à matriz Mc Donuts. O estudante decidiu manter esse bloco na Mc Donuts e **alterar somente a Açaí Kids para `192.168.11.0/24`**, para que o ISP possa distinguir as duas redes por roteamento comum. Essa alteração deve ser explicada ao professor na entrega; não é um endereço fornecido pelo PDF. Os enlaces Mc Donuts `192.168.30.0/24` e `192.168.50.0/24` permaneceram com máscara `/24`, conforme o PDF.

## Endereçamento usado na sessão

Os endereços de rede vêm do PDF, exceto a LAN renumerada da Açaí. Os IPs individuais, início dos pools DHCP e domínios foram escolhidos para esta implementação. Os nomes exatos das interfaces físicas dos roteadores ainda precisam ser transcritos do Packet Tracer.

| Local | Rede LAN | Gateway | Servidor | DHCP a partir de | DNS entregue ao PC |
|---|---|---|---|---|---|
| ISP Conect | `172.16.1.0/24` | `172.16.1.1` | `172.16.1.2` | `172.16.1.100` | `172.16.1.2` |
| Show matriz | `192.168.1.0/24` | `192.168.1.1` | `192.168.1.2` | `192.168.1.100` | `172.16.1.2` |
| Show filial | `192.168.2.0/24` | `192.168.2.1` | `192.168.2.2` | `192.168.2.100` | `172.16.1.2` |
| Açaí Kids | `192.168.11.0/24` | `192.168.11.1` | `192.168.11.2` | `192.168.11.100` | `192.168.11.2` |
| Mc matriz | `192.168.10.0/24` | `192.168.10.1` | `192.168.10.2` | `192.168.10.100` | `172.16.1.2` |
| Mc Filial 01 | `192.168.20.0/24` | `192.168.20.1` | `192.168.20.2` | `192.168.20.100` | `172.16.1.2` |
| Mc Filial 02 | `192.168.40.0/24` | `192.168.40.1` | `192.168.40.2` | `192.168.40.100` | `172.16.1.2` |

| Enlace | Rede | Lado da matriz/ISP | Lado do cliente/filial | Estado |
|---|---|---|---|---|
| Show matriz ↔ filial | `192.168.3.0/30` | Matriz `192.168.3.1` | Filial `192.168.3.2` | Testado |
| Mc matriz ↔ Filial 01 | `192.168.30.0/24` | Matriz `192.168.30.1` | Filial `192.168.30.2` | Testado |
| Mc matriz ↔ Filial 02 | `192.168.50.0/24` | Matriz `192.168.50.1` | Filial `192.168.50.2` | Testado |
| ISP ↔ Show matriz | `172.16.2.0/30` | ISP `172.16.2.1` | Show `172.16.2.2` | Testado |
| ISP ↔ Açaí Kids | `172.16.3.0/30` | Pendente | Pendente | Não montado |
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

Registros DNS usados: `www.ispconect.com` → `172.16.1.2`, `www.showdecacau.com` → `192.168.1.2`, `www.mcdonuts.com` → `192.168.10.2`. Na Açaí, o DNS local resolve `www.acaikids.com` → `192.168.11.2`; o registro ainda não foi adicionado ao DNS do ISP.

## Próximo passo e revisão

1. Conectar a Açaí ao ISP por `172.16.3.0/30`, configurar rotas de ida e retorno e testar por IP.
2. Adicionar `www.acaikids.com` → `192.168.11.2` ao DNS do ISP, atualizar o DNS no DHCP da Açaí, renovar o PC e testar sites por nome entre todas as empresas.
3. Conferir IP, máscara, gateway e DNS dos hosts; registrar nomes das interfaces, `show ip route` dos roteadores e testes finais. Salvar o `.pkt`.
