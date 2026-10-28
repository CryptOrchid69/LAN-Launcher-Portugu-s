RICOCHET Anti Traição README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

RICOCHET Anti Cheat é a iniciativa Call of Duty anti fraude. É projetado como um programa de proteção em camadas para títulos Call of Duty e Warzone, combinando detecção lateral do servidor, proteção lateral do cliente, equipes de investigação, segurança da conta e ferramentas de rompimento.

Desenho geral

RICOCHET não é uma única característica. É um programa feito de várias camadas. Algumas camadas são executadas no PC do jogador, algumas são executadas em servidores de jogos, e algumas são tratadas por equipes de segurança que investigam relatórios, analisam telemetria e perseguem vendedores de fraude.

Componente do cliente

No PC, o RICOCHET inclui um driver de nível do kernel para títulos de Call of Duty suportados. Este driver ajuda a detectar ou bloquear adulterações que podem ocorrer abaixo da visibilidade normal do nível de aplicação. Pretende-se executar enquanto os jogos protegidos estão ativos e apoiar decisões de jogo justo com sinais técnicos.

Análise do lado do servidor

Uma parte importante do RICOCHET é o monitoramento lateral do servidor. O jogo pode comparar ações do jogador, padrões de batida, movimento, histórico de contas, dados de correspondência, relatórios de dados e comportamento impossível contra os limites esperados. A análise lateral do servidor é importante porque algumas fraudes tentam se esconder do cliente local, mas ainda criam jogabilidade não natural.

Mitigações

RICOCHET é conhecido por utilizar mitigação. Uma mitigação é uma perturbação no jogo aplicada a suspeitos trapaceiros para reduzir a sua capacidade de prejudicar jogos enquanto a análise adicional continua. Os exemplos descritos publicamente pela Activision ao longo do tempo incluem a redução do impacto dos danos ou a limitação da vantagem desleal. Os métodos exatos mudam e não são totalmente divulgados.

Segurança da conta

RICOCHET também trabalha com confiança na conta. A verificação telefônica, a segurança da plataforma, o histórico da conta e a execução contra os infratores repetidos podem ajudar a reduzir a evasão da proibição. O objetivo não é apenas pegar uma fraude uma vez, mas também tornar o retorno com uma nova conta mais difícil.

Execução

Os possíveis resultados incluem acesso bloqueado, remoção de fósforos, restrições temporárias, proibições permanentes, remoção de leaderboard e ação contra desenvolvedores ou revendedores. A Activision também usa ações legais e comerciais contra redes de fraude.

Conselhos do jogador

Mantenha os recursos de segurança do sistema ativados quando necessário, evite ferramentas de terceiros que modificam a memória do jogo, não use ferramentas de desbloqueio, scripts de controle, sobreposições suspeitas, spooofers ou serviços de aumento de conta. Use suporte oficial de Activision para recursos ou problemas de segurança da conta.

[Plano geral do produto]
* Desenvolvedor: Activision / Call of Duty Studio SPEAR Team (Internal)
* Arquitetura: Sistema Multi-Tiered (Kernel-Level PC Driver + Servidor-Side Machine Learning)
* Lançamento operacional: Final de 2021 (coincidindo com CoD: Vanguard & Warzone Caldera)
* Filosofia Core: Prevenção ativa de camadas combinando limites profundos do kernel local do sistema operacional
com telemetria do lado do servidor, mitigação comportamental dinâmica e fraude proativa
Investigação.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA & OPERAÇÃO DE SISTEMAS
------------------------------------------------------------------------------------------------------------------
* Kernel Privileges (Ring 0): Em plataformas de PC, Ricochet implementa um alto privilégio
controlador do sistema operativo. Este driver valida processos de sistema ativo, ganchos,
e manipula a aplicação antes que eles possam tocar a memória do cliente do jogo.
* Pegada do sistema: Gerencia a infraestrutura central através de binários localizados e dinâmicos:
- Directório Local: `C:\Program Files (x86)\Call of Duty` (ou a raiz da sua plataforma)
- Driver Payload: Carregado e atualizado dinamicamente através do Battle.net ou Steam
cliente runtimes em vez de registrar um driver de inicialização permanente e estático do Windows.
* Lifecycle Boundary: O driver de modo kernel opera estritamente sob demanda,
ciclo de vida ligado ao jogo. Inicia na memória quando um cliente protegido Call of Duty
lança e descarrega completamente seus ganchos no momento em que o processo de jogo sai.

------------------------------------------------------------------------------------------------------------------
2. MATRIX DE SEGURANÇA E MITIGAÇÃO IN-GAME
------------------------------------------------------------------------------------------------------------------
Ricochet é altamente único para seus frameworks proativos de "mitigação", que degradam
Capacidades dos batoteiros em tempo real para coletar telemetria em vez de banir instantaneamente:

* Escudo de Danos: Detecta rastreamento em tempo real, impossível e clips dinâmicos
Os danos do batoteiro são nulos, tornando as balas inofensivas para jogadores justos.
* Cloaking: Instantaneamente obscurece os jogadores legítimos de um campo de fraude detectado
de vista. Jogadores justos, modelos visuais e pegadas de áudio tornam-se completamente invisíveis
para o usuário explore.
* Desarmar: Automaticamente tira um trapaceiro sinalizado de suas armas no meio do jogo, deixando
eles completamente indefesos durante um combate ao vivo.
* Alucinações: Implanta o fantasma, os jogadores clone controlados por IA para o espaço de jogo.
Estas iscas simulam movimentos reais do jogador e parecem idênticas a ferramentas de fraude,
Enganá-los para confirmar telemetria.
* Splat: Desativa dinamicamente o pára-quedas de um trapaceiro durante a implantação, enviando
eles diretamente para o solo, ou multiplica métricas de gravidade média-velocidade para instantaneamente
Esmagar o seu modelo de jogador.

------------------------------------------------------------------------------------------------------------------
3. MONTANTES DE COMPATIBILIDADE E DEPENDÊNCIAS DE KERNEL
------------------------------------------------------------------------------------------------------------------
* Motor de Isolamento de Hardware: Usa mapeamento avançado HWID (Hardware Identifier)
para rastrear e bloquear estruturas maliciosas do sistema fora de matchmaking permanentemente.
Proibições graves ou manipulação de hardware desencadeiam proibições instantâneas de conta após a criação.
* Absolute Linux / Valve Proton Block: Ricochet se recusa explicitamente a operar em
Distribuição Linux, ambientes do Steam Deck ou camadas de vinho. Porque estes
sistemas não fornecem canais nativos de verificação do kernel do Windows, Call of Duty
títulos usando Ricochet bloquear completamente matchmaking nestas configurações.
* Sinergia da Aplicação Host: Co-compilado nativamente dentro do invólucro central de execução
do jogo. Não é executado como um processo de gerenciamento de tarefas independente distinto,
Redução do risco de cessação ou adulteração externa.

------------------------------------------------------------------------------------------------------------------
4. PIPELINA SISTEMÁTICA DE DEPLOYMENT
------------------------------------------------------------------------------------------------------------------
Ricochet é a exclusiva camada de segurança para a primeira franquia de tiro da Activision:
* Call of Duty: Warzone
* Call of Duty: Modern Warfare III
* Call of Duty: Black Ops 6
* Call of Duty: Modern Warfare II (2022)
* Call of Duty: Vanguard

------------------------------------------------------------------------------------------------------------------
5. GUIA DE REPARAÇÃO DE SERVIÇO MANUAL
------------------------------------------------------------------------------------------------------------------
Porque Ricochet é modular e depende muito do lançador principal para soltar
e gerenciar seus estados de driver, dados de jogo corrompidos ou configurações desatualizadas do Windows
pode causar falhas de inicialização. Use estas etapas para reparar seu estado:

PASSO A: Re-Trigger the Launcher Driver Drop
1. Feche completamente o seu cliente de jogo e o seu lançador de plataforma (Battle.net ou Steam).
2. Clique com o botão direito do mouse no ícone do desktop da plataforma (por exemplo, Battle.net) e selecione "Execute como Administrador".
3. Para o vapor: Ir para a biblioteca -> Botão direito do mouse Chamada do dever -> Propriedades -> Ficheiros Instalados
-> Clique em "Verificar a integridade dos arquivos de jogo".
4. Para Battle.net: Selecione Chamada de Dever -> Clique no ícone de engrenagem ao lado do botão Jogar
-> Clique em "Scan and Repair". Isto força o motor a limpar ganchos anti-fraude velhos.

PASSO B: Verifique as configurações de segurança e isolamento do Windows
1. Pressione a tecla do Windows, digite "Isolação da Core", e abra o painel de configurações do sistema.
2. Certifique-se de que "Memory Integrity" é alternado para ON. Ricochet utiliza hipervisor moderno
ganchos de segurança que entram em conflito com os sistemas operativos que funcionam sem verificação ou
drivers maliciosos de terceiros.

PASSO C: Eliminando blocos de software de entrada de mouse e teclado
1. Ricochet agressivamente blacklists não aprovado camadas de virtualização de entrada ou hardware
macros (como dispositivos cronus ou configurações legadas de reWASD).
2. Se o seu cliente jogo quebra instantaneamente para o desktop na inicialização sem um código,
desinstalar o reWASD ou qualquer controlador/remappers de terceiros especializados,
então reinicie o seu sistema.
========================================================================================