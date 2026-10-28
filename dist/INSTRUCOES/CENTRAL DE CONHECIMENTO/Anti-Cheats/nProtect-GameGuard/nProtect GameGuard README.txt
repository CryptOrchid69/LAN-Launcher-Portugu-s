nProtect GameGuard README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

nProtect GameGuard é um produto de segurança de jogos on-line da Internet INCA. É comumente usado por jogos online para proteger o cliente do jogo, bloquear ferramentas de hacker conhecidas, e reduzir botting, adulteração e automação não autorizada.

Desenho geral

GameGuard começa com o jogo protegido e carrega componentes de segurança que monitoram o ambiente do jogo. Ele pode atualizar-se como novos padrões de fraude aparecem. Se o GameGuard não puder começar corretamente, o jogo protegido pode recusar o lançamento ou pode fechar durante o jogo.

Protecção do cliente

Em um nível conceitual seguro, o GameGuard pode assistir a memória do jogo, interação de processos, módulos suspeitos, arquivos alterados, automação de entrada anormal, ferramentas de hacker conhecidas, manipulação de velocidade e tentativas de interferir com o jogo protegido. Ele também pode usar anti malware estilo padrão de detecção para ferramentas associadas com batota.

Autoprotecção

Anti fraude sistemas muitas vezes proteger-se porque ferramentas de fraude pode tentar parar o anti fraude primeiro. GameGuard pode usar ideias de auto-proteção, como proteger seus arquivos, verificar sua própria integridade, e reagir quando outro programa tenta desativá-lo ou alterá-lo.

Por que ele pode se sentir intrusivo

GameGuard tem uma reputação de ser rigoroso porque ele corre profundamente o suficiente para observar o comportamento sensível do sistema em torno do jogo. Isso pode causar conflitos com ferramentas de acessibilidade, sobreposições, software de segurança, ferramentas macro e alguns drivers. O objetivo é a proteção do jogo, mas problemas de compatibilidade podem acontecer.

Papel do editor

O editor do jogo decide como o GameGuard é usado nesse título. Um jogo pode configurar bloqueios mais rigorosos, enquanto outro pode focar no registro e revisão. O editor também controla a disciplina da conta na maioria dos casos.

Execução

GameGuard pode bloquear a inicialização, fechar o jogo, relatar deteções suspeitas ou ajudar o editor a aplicar bans. Ele também pode produzir códigos de erro quando os arquivos estão faltando, bloqueados por antivírus ou incapazes de atualizar.

Conselhos do jogador

Use instaladores de jogos oficiais, mantenha exclusões antivírus limitadas e apenas quando recomendado pelo suporte oficial, evite ferramentas macro e editores de memória, e reinicie após atualizações se o GameGuard perguntar. Para desinstalar ou reparar, use as instruções oficiais do GameGuard ou do editor de jogos.

]
* Classificação do núcleo: Kernel-Level (Ring 0) Anti-Cheat & Anti-Malware Rootkit
* Era Operacional: Ativo desde o início dos anos 2000; utiliza fortemente o legado
e arquiteturas modernas kernel-hooking para proteger B2B2C espaços de jogo online.
* Missão Primária: Interceptando modificação de memória ativa, bloqueando periférico
automação (macros), e validação da integridade binária do jogo através do sistema operacional direto
e manipulação de API.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA E FOTPRINT OPERACIONAL
------------------------------------------------------------------------------------------------------------------
* High-Privilege Driver: lança um persistente Ring 0 driver de dispositivo projetado para
monitorar, interceptar e bloquear solicitações de API não autorizadas no nível do kernel do Windows.
* Core System Binários: Solta e gerencia arquitetura de segurança localizada:
- Directórios locais: Normalmente estruturados dentro de `<game-root-dir>\bin\GameGuard\`
ou `<game-root-dir>\tools\`.
- Drivers para Windows: Instala `npggmsfk.sys`, `npngasfk.sys' ou relacionado `nProtect'
configurações do dispositivo dentro de `C:\Windows\System32\drivers`.
- Binários de Gerente Local: Executa `GameMon.des` (o módulo de monitor principal) ao lado
`w9xpopen.exe' e `dump *.dmp` embrulhos de depuração.
* Dynamic Update Hooking: Cada inicialização obriga o cliente a baixar
e verificar novas configurações de regras e patches de assinatura do INCA
Internet Content Delivery Network (CDN) antes de permitir a liberação do cliente-jogo.

------------------------------------------------------------------------------------------------------------------
2. REGRAS DE SEGURANÇA E DE PROTECÇÃO RIGIDA
------------------------------------------------------------------------------------------------------------------
nProtect GameGuard opera usando rotinas altamente agressivas e invasivas do lado do cliente
Para congelar processos de terceiros maliciosos:

* Shrouding de memória de baixo nível: Monitores e bloqueia as páginas RAM jogo contra dinâmica
manipulação de alocação de memória (bloqueando scanners de memória comuns como Cheat Engine).
* Automated Macro Supressão: Actively gotas ou interceptar entradas de hardware / software
originados de gravadores de teclado não verificados, macros automáticas do rato ou virtuais
Motoristas periféricos.
* Agressivo processo Blacklisting: Características de uma lista interna, codificada de não aprovado
programas de formação. Se aparecer configurações de depuração activas, sobreposição não verificada
injetores, ou diagnósticos de monitoramento do sistema, termina
programa ofensivo ou o próprio cliente do jogo.
* Direct Kernel Hooking: Restringe certas chamadas vitais da API do sistema Windows para parar
processos não confiáveis de gerar manipuladores ou strings de consulta do processo de jogo.

------------------------------------------------------------------------------------------------------------------
3. MONTANTES DE COMPATIBILIDADE E REPERCUSSÕES DE SISTEMA
------------------------------------------------------------------------------------------------------------------
* Sistema de Agressão Legacy: Devido ao seu design histórico intrusivo, GameGuard é
conhecido por causar blocos de software "exclusão mútua". Foi documentado
quebrando, bloqueando, ou equivocando aplicativos mainstream como navegadores da web,
Clientes VoIP (Discord), camadas de streaming, ou controladores de sobreposição personalizados.
* Linux / Valve Suporte Próton: Embora inerentemente um produto do kernel centrado no Windows,
recentes implantações modernas adicionaram camadas estruturais de apoio para possibilitar a tradução
compatibilidade com a camada Proton da Valve, permitindo execução no Steam Deck / SteamOS
Para títulos principais específicos.
* Antivirus Falso Positivos: Porque o GameGuard injeta-se em funções OS e
emprega comportamento de monitoramento tipo rootkit, software de segurança de terceiros
(como o Windows Defender, Avast ou Bitdefender) frequentemente coloca seus módulos em quarentena,
causando falhas de inicialização de inicialização.

------------------------------------------------------------------------------------------------------------------
4. INTEGRAÇÕES RECENTE E HISTÓRICO DO ECOSSISTEMA
------------------------------------------------------------------------------------------------------------------
GameGuard continua a ser um enorme grampo de arquiteturas de segurança de jogos online sul-coreanos,
e protege várias propriedades globais multijogador:
* Helldivers 2
* Blade & Soul
Esquadrão Negro
* Undecember
* Elsword
* Lineage / Lineage II
* Phantasy Star Online 2 (implantações Legacy antes das atualizações do motor)
* Ragnarok Online (variantes de implantação Legacy)

------------------------------------------------------------------------------------------------------------------
5. MANUTENÇÃO, REPARAÇÃO e GUIA DE LIMPEZA MANUAL
------------------------------------------------------------------------------------------------------------------
Transferências de servidor paralisadas ou blocos de cache corrompidos frequentemente lançam loops de erro
(como códigos de erro 114, 340, 360 ou 380). Use estes passos exatos para resolver ou
Limpe o software inteiramente:

PASSO A: Execute Ferramentas Integradas de Limpeza de Desenvolvedor
1. Abra o diretório de instalação estrutural do seu jogo (por exemplo, via Steam: Botão direito do mouse
jogo -> Gerenciar -> Procurar arquivos locais).
2. Procure uma subpasta designada como “tools” ou “GameGuard”.
3. Localize e execute `gguninst.exe' ou `GGUninstall' como administrador para naturalmente
desengatar os serviços do sistema central.

PASSO B: Forçando a Reconstrução de uma Pasta Limpa (erros de atualização de arquivos)
1. Navegue diretamente para o caminho de execução root do seu jogo (por exemplo, `...\common\Helldivers 2\bin\`).
2. Localize a pasta explicitamente chamada `GameGuard' e exclua-a inteiramente.
3. Abra o lançador do jogo (como o Steam), clique com o botão direito nas propriedades do jogo, selecione
"Arquivos Instalados", e clique em "Verificar a integridade dos arquivos de jogo". Isto força o
sistema para baixar novos binários de base não corrompidos.

PASSO C: Limpeza manual do serviço do Windows
1. Se o jogo for removido, mas os restos de fundo permanecem, abra o Prompt de Comando do Windows
como administrador.
2. Execute os seguintes comandos de terminal para remover registros de serviço:
sc stop npggsvc
sc apagar npggsvc
3. Reinicie seu PC para desbloquear totalmente objetos de driver persistentes na memória.
4. Navegue para `C:\Windows\System32\drivers` e remova permanentemente arquivos correspondentes
o perfil 'npgg*.sys'.
========================================================================================