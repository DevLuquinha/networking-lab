# Roteiro de apoio — Lab 04

**Estado: preparado, ainda não iniciado.** Este roteiro organiza a tentativa sem entregar endereços individuais, comandos ou configurações. O [enunciado](assignment.md) é a referência dos requisitos e dos pontos. A primeira ação, quando Lucas disser que vai iniciar, é um **inventário textual** das LANs, enlaces, serviços e dispositivos; o desenho lógico e físico exigido pelo professor vem durante a montagem.

Se a tentativa for feita como simulado, Lucas inicia seu próprio cronômetro de 120 minutos e usa um `.pkt` novo. O mentor acompanha **uma etapa por vez** e não presume que um teste funcionou sem saída, captura ou relato específico. Pergunte a hipótese antes de um teste; se Lucas pedir uma solução direta, entregue-a com explicação. Depois do simulado, revise o que faltou sem alterar retroativamente a pontuação da tentativa.

| Etapa | Trabalho de Lucas | Evidência para conferir |
|---|---|---|
| 0. Interpretar | Escolher duas empresas de Transportes e listar, em texto, os segmentos e serviços exigidos; separar dados do PDF de escolhas próprias. | Inventário e nomes dos clientes; redes do PDF identificadas sem sobreposição. |
| 1. Planejar | Definir IPs de interfaces e servidores, gateways, pools DHCP, nomes de domínio e dois enlaces ISP–cliente. | Tabela com IP, máscara, gateway e DNS esperado por LAN; IPs utilizáveis nos enlaces `/30`. |
| 2. Montar matrizes | Montar DTI, ADM e DVEN de cada cliente; configurar DHCP, DNS e Web. | Amostras dos quatro PCs de cada matriz com DHCP; site local aberto por IP e URL a partir dos departamentos. |
| 3. Ligar filiais | Montar DTI e departamento de cada filial, o enlace `/30` e caminhos de ida e retorno. | DHCP local dos PCs; interfaces e rotas verificadas; site da própria matriz aberto por URL em cada filial. |
| 4. Montar ISP | Criar LAN, Web, DNS/DHCP e ligações aos dois clientes. | DHCP do PC do ISP; site com planos e valores; URLs do ISP e dos clientes resolvidas e abertas a partir das redes previstas. |
| 5. Conferir isolamento e HTTPS | Testar o acesso permitido aos sites e um acesso direto não previsto à rede do outro cliente. Separar testes HTTP e HTTPS. | Origem, destino, protocolo e resultado exato de cada tentativa; explicação de como o isolamento foi obtido. Registrar limites observados do Packet Tracer, se houver. |
| 6. Fechar | Salvar configurações e `.pkt`; apresentar topologia lógica e física; explicar DNS e Web no caminho de ida e volta. | [Modelo de evidências](evidence-template.md) preenchido e dúvidas registradas para revisão posterior. |

**Critério de estudo:** uma página abrir no navegador confirma aquele acesso observado; não comprova por si só DHCP, DNS, HTTPS, rotas de retorno ou isolamento. Quando algo falhar, compare IP/máscara/gateway/DNS do host, estado das interfaces, tabela de rotas, resolução de nome e serviço Web, nessa ordem conforme o sintoma.

**English practice:** *headquarters* = matriz, *branch office* = filial, *web server* = servidor Web, *access control* = controle de acesso. Ao final, tente explicar uma das verificações em uma frase curta em inglês ou misturando os idiomas.
