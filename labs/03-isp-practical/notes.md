# Notas e evidências — ISP

## Inventário inicial

Fonte: [enunciado](assignment.md). O trabalho está na etapa de interpretação; ainda não há `.pkt` nem testes deste lab.

| Local | LAN ou enlace | Estado |
|---|---|---|
| ISP Conect | `172.16.1.0/24` | Previsto no PDF |
| ISP ↔ Show de Cacau | `172.16.2.0/30` | Previsto no PDF |
| ISP ↔ Açaí Kids | `172.16.3.0/30` | Previsto no PDF |
| ISP ↔ Mc Donuts | `172.16.4.0/30` | Previsto no PDF |
| Show de Cacau | `192.168.1.0/24`, `192.168.2.0/24`, enlace `192.168.3.0/30` | Previsto no PDF |
| Açaí Kids | `192.168.10.0/24` | Previsto no PDF; sobrepõe Mc Donuts |
| Mc Donuts | `192.168.10.0/24`, `192.168.20.0/24`, `192.168.40.0/24`; enlaces `192.168.30.0/24` e `192.168.50.0/24` | Previsto no PDF; sobreposição e máscaras a confirmar |

## Endereçamento escolhido

Pendente: preencher conforme a topologia for construída. Separar endereço de rede, IP da interface, máscara, gateway e faixa DHCP.

## Testes observados

Pendente. Registrar dispositivo de origem, destino, comando ou URL, resultado e hipótese quando falhar.

## Dúvidas para confirmar

- Qual dos blocos `192.168.10.0/24` das empresas deve mudar, ou há intenção de usar tradução de endereços?
- Os enlaces de Mc Donuts devem permanecer `/24`, conforme o PDF, ou o professor espera `/30` como nos demais enlaces ponto a ponto?
