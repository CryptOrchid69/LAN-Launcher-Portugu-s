README PunkBuster

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

PunkBuster é um dos mais antigos jogos de PC anti fraude sistemas. Foi desenvolvido pela Even Balance e foi amplamente utilizado em jogos online anteriores e jogos multiplayer. Seu objetivo é detectar software trapaça e remover jogadores trapaceadores de servidores protegidos.

Desenho geral

PunkBuster é integrado ao cliente do jogo e servidor de jogo. O componente lateral do cliente é executado na máquina do jogador e se comunica com o componente lateral do servidor. Os administradores de servidores podem usar ferramentas PunkBuster para gerenciar servidores protegidos, revisar mensagens de violação e impor chutes ou proibições.

Verificações de clientes

Em um nível conceitual seguro, o PunkBuster pode digitalizar a memória, inspecionar arquivos relacionados ao jogo, procurar assinaturas de fraude conhecidas, verificar determinadas configurações do cliente e verificar se o componente de proteção local está atualizado. Ele também pode usar screenshots ou servidores solicitados verificações dependendo da configuração do jogo.

Função de administrador do servidor

PunkBuster tornou-se popular em parte porque deu aos administradores de servidor ferramentas diretas. Os administradores poderiam configurar regras, receber avisos de violação, chutar jogadores e gerenciar listas de ban. Isso o tornou útil para servidores hospedados na comunidade, especialmente em jogos antigos.

Atualizações

PunkBuster usa um sistema de atualização para que os arquivos de proteção possam mudar conforme novas fraudes aparecem. Se o cliente ou servidor estiver desatualizado, os jogadores podem ser chutados mesmo que não estejam traindo. Muitos problemas do PunkBuster em jogos antigos são causados por serviços desatualizados, arquivos ausentes, blocos de firewall ou configuração antiga do servidor.

Execução

A execução pode incluir avisos, chutes, proibições específicas de jogos, proibições globais e restrições relacionadas com hardware em casos graves. Os administradores de servidores também podem manter listas de ban locais separadas das ações globais.

Pontos fortes e fracos

PunkBuster ajudou a definir o início on-line anti fraude execução. Sua idade significa que pode ser menos comum em novos jogos, e instalações mais antigas podem ser frágeis em sistemas Windows modernos. Ainda é importante historicamente e ainda aparece em algumas comunidades de jogo legado.

Conselhos do jogador

Use arquivos de jogo oficiais, atualize PunkBuster apenas de fontes oficiais, evite ferramentas de fraude e editores de memória, e verifique permissões de firewall se um jogador limpo está sendo chutado para erros de comunicação.

[Plano geral do produto]
* Desenvolvedor: Even Balance, Inc. [evenbalance.com]
* Arquitetura: Dual-Service Client/Server Architecture (User-Mode + Driver)
* Classe operacional: Historicamente significativo pioneiro do anti-roubo consumidor
* Filosofia Core: Varredura contínua em tempo real de espaço de memória, fundo
rastreamento de processos e verificação automatizada de integridade de arquivos emparelhados com
Pesquisa do servidor Master Server.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA E FOTPRINT OPERACIONAL
------------------------------------------------------------------------------------------------------------------
* Arquitetura de serviço duplo: Em sistemas Windows, PunkBuster divide seu tempo de execução
responsabilidades em dois serviços de base distintos que funcionam constantemente
Manter os circuitos de comunicação:
- PnkBstrA: O serviço do sistema base (`PnkBstrA.exe`). Ele inicializa com
Janelas para lidar com comunicações, atualizações dinâmicas e apertos de mão de detecção de jogos.
- PnkBstrB: O serviço de monitoramento ativo (`PnkBstrB.exe`). Começa dinamicamente
quando um executável de jogo protegido por PunkBuster carrega para executar varreduras de memória.
* High-Privilege Helper Driver: Instala um controlador de monitoramento especializado no
sistema de arquivos, tipicamente chamado `pbcl.sys` ou `pbsv.sys` dentro de diretórios protegidos.
* Pegada de disco: Gerencia binários do sistema principal em dois locais primários:
- Caminhos do sistema: `C:\Windows\System32\` ou `C:\Windows\SysWOW64\`
- Local Game Paths: Contido dentro de uma pasta `<game-root-dir>\pb\` localizada.

------------------------------------------------------------------------------------------------------------------
2. ASSUNTOS DE SEGURANÇA E LEGACY EXPLOIT MITIGAÇÃO
------------------------------------------------------------------------------------------------------------------
O PunkBuster opera utilizando uma abordagem mais antiga e altamente estruturada para prevenir, capturar,
e penalizar a integração ilícita de software de terceiros:

* Verificação de Memória Direta: continuamente loops através do cliente do jogo ativo
Endereços RAM para localizar padrões conhecidos de fraude, injetores não autorizados, ou ganchos de gancho.
* Global Blacklisting Database: Corre em execução strings processo de fundo e MD5
arquivos hashes contra um extenso dicionário de assinaturas atualizado por analistas de Even Balance.
* Dynamic PunkBuster Screenshots: Apresenta uma opção única permitindo servidores de jogo
para silenciosamente alertar clientes locais para capturar e carregar uma imagem JPEG em tempo real
seu buffer de tela no jogo para detectar sobreposições visuais de wallhack e ESP.
* Guid & Hardware Enforced Bans: Combina identidades CD-Key únicas com estrutural
índices biométricos de hardware (PB GUID) para isolar e excluir permanentemente maliciosos
jogadores através de listas de ban global (Master Server Blacklists).

------------------------------------------------------------------------------------------------------------------
3. MONTANTES DE COMPATIBILIDADE E DESAFIOS DE SYNC
------------------------------------------------------------------------------------------------------------------
* Auto-Update Motores: PunkBuster carece de um auto-updater moderno e unificado.
Se um jogador reinstalar um título legado através de storefronts de distribuição digital (como o Steam),
o jogo frequentemente empacota uma versão antiga do PB que não consegue se conectar com servidores ao vivo,
causando chutes instantâneos (por exemplo, "Losing Key Packets").
* Fragilidade do pacote de rede: Altamente sensível às configurações de firewall, rede localizada
latência e perda de pacotes. Se `PnkBstrB.exe` encontrar um breve atraso de encaminhamento quando
comunicando com `PnkBstrA.exe`, o servidor de jogo chuta instantaneamente o jogador.
* Modern OS e Linux Limites: Porque ele depende de gerenciamento de serviços Windows mais antigo e rígido
e ganchos de API profundos, ele enfrenta problemas de compatibilidade maciça sob o Proton Linux da Valve
camada, tornando Linux/Steam Deck suporte em jogos multiplayer mais antigos um ponto comum de falha.

------------------------------------------------------------------------------------------------------------------
4. DEPLOIOS HISTÓRICOS E RECENTES
------------------------------------------------------------------------------------------------------------------
PunkBuster serviu como espinha dorsal para jogos competitivos para PC no início dos anos 2000:
* Battlefield 4 / Battlefield 3 / Battlefield: Bad Company 2
* Battlefield 2142 / Battlefield 2 / Battlefield 1942
* Call of Duty 4: Guerra Moderna / Call of Duty 2 / Call of Duty (Original)
* Medalha de Honra (2010 / Guerreiro)
* Exército da América (Deploys Legacy)
* Cry distante / Cry distante 2
* Wolfenstein: Território Inimigo

------------------------------------------------------------------------------------------------------------------
5. MANUTENÇÃO, REPARAÇÃO, & PROCEDIMENTOS DE ATUALIZAÇÃO MANUAL
------------------------------------------------------------------------------------------------------------------
Devido à natureza frágil de arquivos de distribuição mais antigos Mesmo Balance, intervenção manual
é frequentemente necessário para resolver loops de conexão ou falhas de execução.

PASSO A: Use a Ferramenta PBSetup oficial independente
1. Navegue para o site oficial do Even Balance e faça o download da ferramenta autônoma `pbsetup.exe`.
2. Botão direito do mouse `pbsetup.exe` e selecione "Execute como Administrador".
3. Clique em "Add a Game", selecione seu título legado alvo do dropdown, e ponto
o caminho do explorador de arquivos para a pasta raiz do jogo.
4. Clique em "Verificar atualizações" para forçar um download limpo, manual do sistema mais recente
definições diretamente no diretório do seu jogo.

PASSO B: Verifique e Corrija Registros de Serviço do Windows
1. Abra a janela Executar (`Windows Key + R`), digite `services.msc` e pressione Enter.
2. Role para baixo para localizar `PnkBstrA' e `PnkBstrB`.
3. Clique duas vezes em ambos os itens, garantir que seu "tipo de início" é configurado para "Automático",
e verificar que o seu estado diz "Correr".
4. Se estiverem bloqueados, abra um Prompt de Comando do Administrador e execute:
sc start PnkBstrA
início do sc PnkBstrB

PASSO C: Purga manual completa
1. Abra um Prompt de Comando do Administrador e execute as seguintes linhas para limpar listas de serviços:
sc parar PnkBstrB
sc excluir PnkBstrB
sc parar PnkBstrA
sc excluir PnkBstrA
2. Reinicie seu computador para liberar quaisquer processos bloqueados.
3. Abra o Windows Explorer e manualmente eliminar todos os executáveis 'PnkBstr*'
drivers localizados dentro de `C:\Windows\System32\` e `C:\Windows\SysWOW64\`.
========================================================================================