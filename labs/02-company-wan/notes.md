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

| Rede / dispositivo | Endereço e máscara escolhidos | Por que escolhi | Conferido no Packet Tracer? |
|---|---|---|---|
| LAN de Uberaba e gateway | | | |
| DNS e Web da matriz | | | |
| Enlace: interface de Uberaba | | | |
| Enlace: interface de Sacramento | | | |
| LAN de Sacramento e gateway | | | |
| DHCP local e intervalo de clientes | | | |

## Etapas 3–6 — previsão, teste e diagnóstico

| Teste | Minha previsão | Resultado observado e evidência | Hipótese ou explicação |
|---|---|---|---|
| DHCP em cada departamento de Sacramento | | | |
| Comunicação dentro da filial | | | |
| Comunicação entre os roteadores | | | |
| PC da filial → DNS da matriz por IP | | | |
| PC da filial → Web da matriz por IP | | | |
| Resolução do nome Web na filial | | | |
| HTTP/HTTPS pelo nome na filial | | | |

## Etapa 7 — explicação final

- **Caminho da consulta DNS e da resposta:**
- **Caminho da requisição Web e da resposta:**
- **Erro que encontrei, hipótese que testei e causa confirmada:**
- **O que ainda não sei explicar:**
- **Uma frase técnica em inglês que pratiquei:**
