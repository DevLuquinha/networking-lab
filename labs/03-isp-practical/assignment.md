# Lab 03 — Preparatório para a prova prática: ISP

## Fontes e objetivo

- Enunciado do professor: `Exercício preparatorio para a prova pratica.pdf` (10 a 23/11/2026).
- [Videoaula: criação e configuração de um ISP](https://www.youtube.com/watch?v=VdqleBOIbRE), 1h43min31s. A transcrição automática foi consultada; nomes e números ditados podem conter erros de reconhecimento.
- Montar no Packet Tracer um ISP local e três empresas clientes, de modo que os sites dos clientes e do ISP possam ser acessados.

Este projeto é independente dos Labs 01 e 02; preserve os arquivos `.pkt` anteriores. Salve a topologia deste trabalho neste diretório.

**Implementação:** a topologia concluída está em [ISP Practical.pkt](ISP%20Practical.pkt); o endereçamento efetivo, os resultados relatados e a revisão final estão em [notes.md](notes.md).

## Escopo explícito do PDF

| Organização | Rede | Bloco |
|---|---|---|
| ISP Conect | Matriz | `172.16.1.0/24` |
| ISP Conect | Ligação com Show de Cacau | `172.16.2.0/30` |
| ISP Conect | Ligação com Açaí Kids | `172.16.3.0/30` |
| ISP Conect | Ligação com Mc Donuts | `172.16.4.0/30` |
| Show de Cacau | Matriz | `192.168.1.0/24` |
| Show de Cacau | Filial | `192.168.2.0/24` |
| Show de Cacau | Ligação matriz–filial | `192.168.3.0/30` |
| Açaí Kids | Matriz | `192.168.10.0/24` |
| Mc Donuts | Matriz | `192.168.10.0/24` |
| Mc Donuts | Filial 01 | `192.168.20.0/24` |
| Mc Donuts | Ligação filial 01 | `192.168.30.0/24` |
| Mc Donuts | Filial 02 | `192.168.40.0/24` |
| Mc Donuts | Ligação filial 02 | `192.168.50.0/24` |

O PDF mostra a topologia lógica das unidades e enlaces, mas não especifica quantidade de PCs, modelo dos roteadores, endereços individuais, domínios ou conteúdo dos sites. Essas decisões devem ser planejadas e registradas, sem atribuí-las ao enunciado.

## Ambiguidades do enunciado e decisão do estudante

1. **Sobreposição:** Açaí Kids e matriz Mc Donuts receberam o mesmo bloco `192.168.10.0/24`. Rotas IP comuns não conseguem distinguir duas redes remotas com o mesmo prefixo. Para a implementação, o estudante decidiu **manter `192.168.10.0/24` na Mc Donuts e usar `192.168.11.0/24` na Açaí Kids**, registrando essa divergência para explicar ao professor na entrega. A tabela acima preserva os blocos originais do PDF.
2. **Máscaras dos enlaces Mc Donuts:** o PDF usa `/24` para `192.168.30.0` e `192.168.50.0`, embora os enlaces entre dois roteadores possam usar `/30`. A implementação manteve `/24`, conforme o PDF.
3. **Vídeo como exemplo:** a aula usa nomes e endereços diferentes (ISP Fred, Burger Show e Bar do Tod). Aproveitar o método, mas usar os blocos do PDF para este trabalho.

## Evidências de conclusão

- Tabela de endereços e interfaces efetivamente usados.
- IP, máscara, gateway e DNS conferidos nos hosts, inclusive após renovar DHCP quando houver mudanças.
- Enlaces e rotas de ida e volta verificados por `ping` e `show ip route`.
- Resolução dos domínios no DNS escolhido e páginas abertas por nome no navegador do Packet Tracer.
- Caminho de uma consulta DNS e de uma requisição Web explicado, incluindo as respostas.

Siga o [roteiro](study-path.md) e registre somente resultados observados em [notes.md](notes.md).
