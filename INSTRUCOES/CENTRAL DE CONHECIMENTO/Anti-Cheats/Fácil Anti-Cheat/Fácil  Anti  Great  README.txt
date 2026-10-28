Fácil Anti fraude README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

Easy Anti Cheat, muitas vezes chamado EAC, é um serviço de segurança de jogo comercial usado por muitos jogos online multiplayer. Seu trabalho é ajudar o editor do jogo a manter as partidas públicas justas, verificando se o cliente do jogo está executando em um estado confiável, se os arquivos de jogo foram alterados de maneiras não autorizadas, e se o software externo está tentando interferir com a jogabilidade normal.

Desenho geral

EAC é geralmente integrado no lançador de jogo e no cliente de jogo. Quando um jogo protegido começa, o processo EAC bootstrap verifica que o serviço de proteção pode carregar, que os arquivos necessários estão presentes, e que o jogo está lançando através de um caminho esperado. Se esta verificação inicial falhar, o jogador geralmente não pode entrar em servidores online protegidos.

O sistema combina verificações do lado do cliente, validação do lado do servidor, telemetria, ferramentas de execução de editor e ações de nível de conta. Componentes do cliente procuram sinais de adulteração. Componentes laterais do servidor ajudam o editor a comparar o comportamento do jogador com as regras de jogo esperadas. A execução pode incluir a prevenção do lançamento, chute de uma partida, restrições temporárias, proibições permanentes ou revisão manual pelo editor.

O que ele costuma ver

EAC geralmente se concentra no processo de jogo protegido, arquivos de jogo, módulos carregados, interação de processo suspeito, drivers suspeitos, acesso de memória incomum, indicadores de depuração e padrões conhecidos de fraude. Ele também pode verificar se os recursos de segurança do sistema operacional estão em um estado que o editor de jogos aceita.

Por que os componentes do nível do kernel podem existir

Muitas fraudes modernas tentam esconder-se sob o software de nível de aplicação normal. Por essa razão, alguns jogos protegidos EAC podem usar componentes de sistema de baixo nível para observar ou bloquear adulteração que o software de nível de usuário comum não pode ver de forma confiável. O comportamento exato depende do jogo, configuração do editor, plataforma e versão atual do EAC.

Como tomar decisões

As decisões anti fraude não são normalmente baseadas em um sinal simples. Um sistema pode combinar assinaturas conhecidas, verificações de integridade, comportamento suspeito, comunicação protegida com servidores, sinais de reputação de hardware e conta, e investigação humana. Os editores muitas vezes evitam detalhes públicos instantâneos porque revelar a lógica de detecção ajuda os desenvolvedores a se adaptarem.

Privacidade e limitações

Um anti fraude grave deve coletar apenas o que ele precisa para a proteção do jogo, mas os jogadores ainda devem tratar qualquer anti fraude como poderoso software de segurança. EAC pode criar conflitos com sobreposições, depuradores, ferramentas de virtualização, drivers antigos, ferramentas de mod e utilitários de sistema incomuns. Os falsos positivos são possíveis, muitos editores fornecem rotas de recurso.

Conselhos do jogador

Mantenha o Windows, drivers gráficos, drivers chipset e o jogo atualizado. Evite executar ferramentas de fraude, editores de memória, injetores desconhecidos, software rachado, sobreposições suspeitas e ferramentas de automação enquanto joga jogos protegidos. Use páginas de suporte oficiais para reparar ou apelar em vez de baixar correções de terceiros.

Preciso que me dês uma READ ME.txt que lista com o máximo de detalhes possível, tudo sobre EA anti batota

[Plano geral do produto]
* Desenvolvedor: Kamu (Adquirido por Epic Games / Epic Online Services)
* Arquitetura: Hybrid Kernel-Level (Ring 0 Driver) + Heurísticas de Modo de Usuário
* Pegada da indústria: 200+ títulos principais, protegendo 35M+ jogadores mensais
* Filosofia Core: Proactive, modular segurança de camadas combinando cliente-lado
proteção de memória com análise comportamental global do lado servidor.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA & OPERAÇÃO DE SISTEMAS
------------------------------------------------------------------------------------------------------------------
* Modelo de Driver Híbrido: No Windows, EAC implementa um driver Ring 0
impedir o acesso não autorizado ao espaço de memória do jogo por hacks de alto privilégio.
* Componentes centrais locais: Registra binários estruturais e arquivos de configuração:
- Diretório Local: `C:\Ficheiros de Programa (x86)\EasyAntiCheat`
- Lançador de serviço dinâmico: `EasyAntiCheat EOS Setup.exe` (Epic Online Services)
- Arquivo do driver do sistema: `EasyAntiCheat.sys` dentro `C:\Windows\System32\drivers`
* Gestão do ciclo de vida: O serviço de motorista opera em um ciclo de vida estritamente limitado.
Ele carrega dinamicamente quando um cliente de jogo autenticado inicializa e completamente
termina suas tarefas do sistema quando o processo do jogo sai com segurança.

------------------------------------------------------------------------------------------------------------------
2. MATRIXA DE SEGURANÇA E ANTI-EXPLOITAÇÃO
------------------------------------------------------------------------------------------------------------------
* Code & RAM encobrimento: pesadamente remove para baixo técnicas de injeção externa por
ofuscando endereços internos de função e seções de RAM de jogo de bloqueio ativo.
* Heuristic Threat Spotting: Usa lógica de anomalia local para capturar desconhecido ou alterado
binários em vez de procurar estritamente por bandeiras de assinatura de arquivos pré-gravadas.
* Conjunto de ameaças compartilhadas: Opera um banco de dados global do lado do servidor. Pegadas de ameaça
manchado em um jogo atualizar automaticamente barreiras de segurança em todos os títulos EAC.
* Isolamento de hardware: Aproveita marcadores biométricos de hardware multiponto (HWID) para
bloqueie permanentemente nós de máquinas maliciosos fora de instâncias matchmaking de rede.
* Restrição de Modding: A integridade estrutural verifica proativamente restringir o jogo local
modificações e scripts personalizados enquanto os estados multiplayer online estão envolvidos.

------------------------------------------------------------------------------------------------------------------
3. COMPATIBILIDADE E LINUX/ESTRATÉGIA DO VINHO
------------------------------------------------------------------------------------------------------------------
* Crossplay Foundations: Escala uniformemente em Windows, macOS, Linux, PlayStation,
Xbox e ambientes Nintendo Switch.
* Suporte ao Deck de Próton e Steam: possui um modo de retrocesso oficial do espaço do usuário construído
para a camada de tradução de Próton da Valve. Os desenvolvedores podem alternar compatibilidade Linux
via Epic Online Services (EOS) sem exigir a compilação nativa do cliente Linux.
* Expansão Estrutural Linux: Para otimizar operações em sistemas não-Windows,
Epic continua a expandir a verificação de compatibilidade vinho/próton nativo, embora
o modo espaço-usuário sacrifica ganchos mais profundos do kernel para permanecer em conformidade com a tradução.

------------------------------------------------------------------------------------------------------------------
4. INTEGRAÇÕES RECENTES E ATIVAS NOTÁVEIS
------------------------------------------------------------------------------------------------------------------
A EAC continua a ser a única ferramenta anti-fraude mais adotada para títulos competitivos:
<br clear=left>== Ligações externas ==
* Apex Legends
* Elden Ring
* Morto pela luz do dia
* As Finais
* Rust
* Rocket League (Integrado para PC componentes de jogo online)
* VRChat

------------------------------------------------------------------------------------------------------------------
5. GUIA DE REPARAÇÃO DE SERVIÇO MANUAL
------------------------------------------------------------------------------------------------------------------
Certificados corrompidos, atualizações dinâmicas ou transferências de arquivos de jogo podem quebrar o
Ligação de serviço. Use esta lista de verificação operacional para reparar ou limpar artefatos:

PASSO A: Execute o utilitário de reparo embutido
1. Navegue diretamente para os arquivos de instalação do seu jogo via Steam ou Epic Games Launcher.
2. Abra a subpasta `EasyAntiCheat` (por exemplo, `Binários\Win64\EasyAntiCheat`).
3. Botão direito do mouse `EasyAntiCheat EOS Setup.exe` e selecione "Execute como Administrador".
4. Selecione o seu jogo específico no menu suspenso da ferramenta e clique em "Serviço de reparação".

PASSO B: reparação de injeção de linha de comando (para gotas de serviço ausentes)
1. Se o jogo falhar apontando para elementos de configuração ausentes, crie um atalho de desktop
de `EasyAntiCheat EOS Setup.exe`.
2. Clique com o botão direito do mouse no atalho -> Propriedades -> Vá para o fim da caixa de texto "Alvo".
3. Anexar um espaço de trilha seguido pela bandeira de implantação apropriada:
- Reparar ganchos padrão: `reparar `
- Para forçar a instalação padrão: ` install prod-fn`
4. Aplique alterações, clique com o botão direito do mouse no atalho e "Execute como Administrador".

PASSO C: Remoção manual do driver do Kernel
1. Open Command Prompt (CMD) como Administrador.
2. Execute os seguintes comandos de terminal para excluir tarefas de serviço persistentes:
sc stop EasyAntiCheat
sc apagar EasyAntiCheat
3. Reinicie o computador para desbloquear ganchos do sistema ativo.
4. Navegue para `C:\Windows\System32\drivers` e delete com segurança `EasyAntiCheat.sys`.
========================================================================================