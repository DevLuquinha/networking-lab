# Roteiro de prática — ISP

Avance por evidências, sem necessidade de seguir um calendário. Primeiro monte um inventário textual; o desenho do Packet Tracer vem depois. Não reutilize o `.pkt` da WAN como trabalho final sem criar uma cópia independente.

| Etapa | Trabalho | Evidência para avançar |
|---|---|---|
| 1. Interpretar o escopo | Conferir as redes do [enunciado](assignment.md), identificar LANs, enlaces e serviços. Marcar sobreposição e demais ambiguidades. | Inventário textual e decisão sobre o que pode ser montado antes do esclarecimento. |
| 2. Planejar endereços | Escolher IPs de interfaces, servidores e pools DHCP sem conflito dentro de cada rede. | Tabela em [notes.md](notes.md), com máscara e gateway de cada segmento. |
| 3. Montar o ISP | Criar LAN, roteador, servidor Web/DNS/DHCP e um PC de teste. | DHCP local, ping e acesso ao site do ISP por nome. |
| 4. Montar Show de Cacau | Criar matriz, filial, DHCP, enlace `/30` e rotas. | Pings entre LANs e acesso ao site da matriz pela filial. |
| 5. Montar Mc Donuts e Açaí Kids | Construir as LANs e enlaces do PDF. Tratar o conflito `192.168.10.0/24` antes de rotear as duas empresas simultaneamente. | Endereçamento e testes locais de cada unidade. |
| 6. Interligar clientes ao ISP | Um enlace `172.16.x.0/30` por cliente, rotas de ida e retorno. | Pings por IP do ISP aos clientes e entre clientes previstos. |
| 7. Integrar DNS e Web | Registrar domínios no DNS do ISP, distribuir o endereço DNS aos clientes e renovar DHCP. | Páginas do ISP e dos clientes abertas por nome. |
| 8. Revisar para a prova | Salvar o `.pkt`, registrar testes e explicar como diagnosticar uma falha de IP, rota, DNS ou Web. | Checklist e evidências em [notes.md](notes.md). |

**Primeiro exercício:** antes de configurar, responda quais redes são locais, quais são enlaces e por que duas empresas com `192.168.10.0/24` criam ambiguidade para o ISP. A partir da resposta, começaremos a tabela de endereços.
