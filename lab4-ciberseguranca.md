d. Laboratório de Cibersegurança e Privacidade:

i. Objetivo do laboratório:

O Laboratório de Cibersegurança e Privacidade tem como objetivo desenvolver pesquisas em segurança de redes, detecção de intrusões, análise de tráfego, resposta a incidentes e proteção de dados em ambientes de alta performance. O laboratório atua como referência em segurança para os demais laboratórios da EEC, estudando ameaças reais sem comprometer o desempenho das aplicações científicas que dependem de baixa latência e alta vazão.

As pesquisas desenvolvidas incluem: análise passiva de tráfego, detecção de anomalias, inteligência contra ameaças (threat intelligence), análise de malware em ambiente controlado, segmentação e microssegmentação, privacidade em compartilhamento de dados de pesquisa, honeypots e validação de políticas de acesso em redes acadêmicas.

ii. Linhas de pesquisa:

1. Detecção de intrusões e análise de tráfego em redes de alto desempenho
2. Segurança em ambientes de computação científica e transferência de grandes volumes de dados
3. Privacidade e anonimização em colaborações internacionais de pesquisa
4. Threat intelligence e correlação de eventos de segurança
5. Segurança em IoT, sistemas embarcados e infraestrutura de borda

iii. Colaboração internacional:

O laboratório mantém colaboração internacional com grupos de pesquisa em segurança de redes e centros de resposta a incidentes acadêmicos (CSIRTs). A parceria envolve troca de indicadores de comprometimento (IoCs), feeds de threat intelligence, amostras de malware para análise em sandbox isolada, relatórios de campanhas de ataque e datasets anonimizados de tráfego para experimentos de detecção.

Também são previstos exercícios conjuntos de resposta a incidentes simulados, nos quais instituições parceiras compartilham logs, alertas e playbooks de mitigação. Esse tipo de colaboração exige sincronização frequente de bases de indicadores, transferência periódica de arquivos de captura (pcap) e comunicação em tempo quase real entre equipes de segurança, sem expor dados sensíveis dos laboratórios de pesquisa da universidade.

iv. Aplicações utilizadas:


| Aplicação                        | Função                                                                |
| -------------------------------- | --------------------------------------------------------------------- |
| Zeek / Suricata                  | análise de tráfego e detecção de intrusões em modo passivo            |
| Wireshark / tshark               | inspeção e análise manual de pacotes                                  |
| Elasticsearch / Kibana           | armazenamento, busca e visualização de logs de segurança              |
| Wazuh                            | correlação de eventos, integridade de arquivos e alertas              |
| MISP                             | compartilhamento estruturado de indicadores de ameaça                 |
| GitLab / Git                     | versionamento de regras, scripts e documentação de incidentes         |
| Cuckoo / ANY.RUN (sandbox local) | análise de malware em ambiente isolado                                |
| pfSense / OPNsense               | firewall e segmentação apenas em zonas de perímetro e administrativas |
| SSH / Bastion host               | acesso remoto controlado aos servidores de análise                    |
| Rsync / Globus                   | transferência de capturas de tráfego e datasets de pesquisa           |
| Videoconferência                 | coordenação de resposta a incidentes com parceiros internacionais     |


v. Infraestrutura física:

1. Estações de trabalho: 10 workstations com processadores de alto desempenho, 64 GB a 128 GB RAM, usadas para análise de tráfego, investigação de incidentes e desenvolvimento de regras de detecção.
2. Servidores de análise: 3 servidores dedicados a coleta de logs, processamento de alertas e execução de motores IDS/NDR; cada servidor com 32 a 64 núcleos, 256 GB RAM e armazenamento NVMe de alta velocidade para indexação.
3. Servidor de sandbox: 1 servidor isolado fisicamente da rede de produção, com 64 núcleos, 128 GB RAM e rede dedicada, para execução controlada de amostras suspeitas.
4. Armazenamento: NAS de 100 TB para retenção de logs, capturas de tráfego (pcap), artefatos de incidentes e backups de configurações de segurança.
5. Rede interna: switch de 24 portas 10 GbE para servidores e estações de análise; switches adicionais de 48 portas 1 GbE para honeypots e equipamentos de teste; uplinks de 10 GbE para o Data Center.
6. Equipamentos de captura: TAPs de rede e portas espelhadas (SPAN) conectadas aos enlaces de saída dos laboratórios de pesquisa e do backbone do campus, permitindo monitoramento passivo sem inserir dispositivos no caminho do tráfego crítico.
7. Equipamentos adicionais: racks, UPS, controle de acesso físico à sala e armário seguro para mídias de backup.

vi. Infraestrutura virtual:

1. máquinas virtuais para serviços de log, bancos de dados de indicadores e ambientes de teste de regras;
2. containers Docker para honeypots, coletores de telemetria e serviços auxiliares de análise;
3. rede virtual isolada (sandbox) sem rota direta para os laboratórios de produção, usada exclusivamente em experimentos com malware;
4. ambiente de SIEM virtualizado para correlação de eventos provenientes dos demais laboratórios da EEC;
5. réplicas de serviços de threat intelligence para consulta local e sincronização periódica com parceiros externos;
6. armazenamento virtualizado para logs e capturas, com política de retenção e descarte automático de dados sensíveis.

vii. Aplicações de rede:

1. Captura passiva de tráfego espelhado dos laboratórios de HPC, IA, embarcados e modelagem climática.
2. Sincronização de feeds de threat intelligence com instituições parceiras.
3. Agregação e correlação centralizada de logs de segurança do campus.
4. Transferência de capturas de tráfego e amostras de malware para análise colaborativa.
5. Alertas em tempo quase real para equipe de resposta a incidentes.
6. Acesso remoto via SSH ao bastion host para administração e investigação.
7. Videoconferência para coordenação de incidentes com CSIRTs parceiros.

viii. QoS do laboratório:


| Aplicação                                       | Banda              | Latência    | Jitter      | Prioridade |
| ----------------------------------------------- | ------------------ | ----------- | ----------- | ---------- |
| Captura passiva de tráfego (SPAN/TAP)           | 1 a 10 Gbps        | irrelevante | irrelevante | crítica    |
| Alertas e correlação em tempo quase real        | 10 a 100 Mbps      | < 50 ms     | baixo       | crítica    |
| Sincronização de threat intelligence (MISP)     | 10 Mbps a 1 Gbps   | < 2 s       | baixo       | alta       |
| Transferência de pcaps e artefatos de incidente | 100 Mbps a 10 Gbps | média       | irrelevante | alta       |
| Indexação e consulta de logs (SIEM)             | 100 Mbps a 1 Gbps  | < 500 ms    | baixo       | média      |
| SSH / Bastion host                              | 1 a 10 Mbps        | < 100 ms    | baixo       | média      |
| Videoconferência (coordenação de incidentes)    | 256 kbps a 4 Mbps  | < 150 ms    | < 1 ms      | alta       |
| Web, Git e e-mail                               | 45 kbps a 10 Mbps  | < 2 s       | irrelevante | baixa      |


ix. Classe de prioridade:


| Classe            | Aplicações                                                                          |
| ----------------- | ----------------------------------------------------------------------------------- |
| EF / CS5 (máxima) | captura passiva de tráfego crítico e alertas de detecção em tempo quase real        |
| AF41              | videoconferência e coordenação síncrona de resposta a incidentes                    |
| AF31              | SSH, bastion host e consultas interativas ao SIEM                                   |
| AF21              | sincronização de threat intelligence, transferência de pcaps e artefatos de análise |
| BE                | web, Git, e-mail e tráfego administrativo não crítico                               |


x. Problema de segurança:

O laboratório opera com tráfego espelhado proveniente dos demais laboratórios de pesquisa, incluindo fluxos de HPC, treinamento de IA, telemetria IoT e transferência científica internacional. Esse tráfego pode conter dados sensíveis de pesquisa e, ao mesmo tempo, precisa ser analisado sem introduzir atraso nas aplicações originais.

Por isso, todo o monitoramento do núcleo da EEC será feito de forma passiva, por TAP ou espelhamento de porta, sem firewall em linha no caminho dos laboratórios de alto desempenho. O laboratório de Cibersegurança concentra as funções de detecção, correlação e resposta, enquanto firewalls tradicionais ficam restritos ao perímetro da universidade, ao acesso de convidados e aos serviços administrativos.

Para reduzir riscos internos ao próprio laboratório, serão adotadas VLANs separadas para análise, sandbox, honeypots, gerência e colaboração externa; ACLs nos switches; autenticação forte; bastion host para acesso remoto; criptografia nas conexões WAN; segregação física/lógica da rede de sandbox; e política de retenção e anonimização de capturas que contenham dados de pesquisa de terceiros.

xi. Justificativa da solução:

A escolha desse laboratório complementa os demais laboratórios da EEC ao tratar segurança como objeto de pesquisa e não apenas como requisito acessório. Enquanto os laboratórios de HPC, IA, sistemas embarcados e modelagem climática dependem de alto desempenho e não podem tolerar inspeção em linha, o laboratório de Cibersegurança assume o papel de monitorar, detectar e responder a ameaças sem interferir no tráfego crítico.

A proposta também atende ao requisito de colaboração internacional, pois prevê troca periódica de indicadores de ameaça, datasets anonimizados e exercícios conjuntos de resposta a incidentes. Do ponto de vista de redes, o laboratório justifica requisitos específicos de QoS para captura passiva, correlação de eventos e transferência de evidências, além de integrar as políticas de segmentação, DiffServ e segurança exigidas pelo projeto do campus.