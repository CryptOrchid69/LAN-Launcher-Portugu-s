ACE Anti Traição README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

ACE Anti Cheat é um sistema de segurança de jogos associado com Tencent e jogos que usam serviços de segurança Tencent. O nome ACE é comumente entendido como Anti Cheat Expert. É usado para proteger os títulos on-line de ferramentas de fraude, abuso de conta, bots e adulteração de clientes.

Desenho geral

A ACE pode combinar proteção lateral do cliente, controle de risco lateral do servidor, reputação da conta, sinais de risco do dispositivo e ferramentas de operações do editor. Em grandes jogos on-line, anti fraude geralmente faz parte de um sistema de segurança maior que também lida com fraude, botting, abuso emulador e roubo de conta.

Protecção do cliente

Em um nível conceitual seguro, ACE pode verificar o processo de jogo protegido, arquivos de jogo, acesso a memória suspeita, módulos não autorizados, ferramentas de automação, clientes modificados, depuração e estados de sistema de risco. O comportamento exato depende do jogo e da plataforma.

Contexto móvel e PC

Tencent jogos relacionados muitas vezes abrangem PC e móvel. Anti trapaça móvel pode focar em dispositivos enraizados, emuladores, arquivos APK modificados, ferramentas de sobreposição, automação, editores de memória e manipulação de rede. PC anti fraude pode se concentrar mais em drivers, código injetado, e adulteração de processo.

Controlo de risco lateral do servidor

Os sistemas de servidor podem detectar resultados de combate impossíveis, ganho de moeda anormal, agricultura automatizada, clusters de dispositivos, compartilhamento de contas e relatórios suspeitos repetidos. A reputação da conta ajuda a identificar infratores repetidos e grupos de fraude organizados.

Execução

Os jogos suportados pela ACE podem bloquear o lançamento, impedir a matchmaking, remover jogadores de jogos, aplicar proibições temporárias ou permanentes, restringir dispositivos ou sinalizar contas suspeitas para revisão. A política do editor controla o resultado exato.

Conselhos do jogador

Use instaladores oficiais, evite clientes modificados, não use dispositivos enraizados ou adulterados para jogos protegidos, a menos que o editor permita, evite ferramentas de automação e use canais de apelação oficiais.

* Arquitetura: multi-camada, segurança multi-plataforma (Kernel Ring 0 no PC)
* Missão: Detecção de exploração em tempo real, endurecimento de dados, e execução fair-play

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA & OPERAÇÃO DE SISTEMAS
------------------------------------------------------------------------------------------------------------------
* Integração Kernel: No PC, ACE opera no Ring 0 (nível Kernel). Bota.
como um controlador de sistema autorizado para proteger a memória e contra hacks de baixo nível.
* Pegada de processo: Registra vários serviços centrais e drivers de sistema:
- Drivers: Nomeado `ACE-*.sys` armazenado dentro de `C:\Windows\System32\drivers`
- Serviços: «ACE-GAME», «ACE-BASE», «AntiCheatExpert Service», e
«Protecção AntiCheatExpert».
* Controle de ciclo de vida: oficialmente projetado para correr ao lado do cliente do jogo.
Ele dorme ou pára de executar uma vez que o processo de host autenticado fecha.

------------------------------------------------------------------------------------------------------------------
2. CARACTERÍSTICAS E CAPACIDADES DA SEGURANÇA DO CORE
------------------------------------------------------------------------------------------------------------------
* Anti-Depuração e Injeção: Bloqueia ferramentas de análise dinâmica, utilitários de gancho,
e injeções em tempo de execução para garantir funções críticas.
* Endurecimento binário: usa frameworks personalizados para complicar local
Esforços de engenharia estática ou reversa.
* Tipos de memória seguros: criptografa tipos de dados de jogo dinamicamente em RAM via
classes proprietárias (por exemplo, saúde de acompanhamento, variáveis monetárias).
* Supressão Speedhack: Identifica e intercepta manipulação sistêmica do relógio,
Terminando instantaneamente aplicações host violando limites de sincronização.
* Bloqueio de máquina virtual: Características de uma lógica de detecção de 3 camadas de identificação
mais de 30 ambientes virtuais (por exemplo, VirtualAPP, LBE, contentores).
* AI Behavioral Analytics: Utiliza modelos de aprendizagem profunda do lado do servidor.
Analisa os pacotes de entrada/replay do usuário para o comportamento mecânico impossível (aimbots,
spinbots) em vez de confiar apenas em correspondências de assinatura de arquivos.

------------------------------------------------------------------------------------------------------------------
3. PARADOXES DE COMPATIBILIDADE E DEPLOYMENT
------------------------------------------------------------------------------------------------------------------
* Cross-Platform SDKs: Integrado nativamente em todos os títulos de PC, Android e iOS.
* Suporte do motor do jogo: Compliance completo wrapper para Unity, Unreal Engine, e
Cocos 2D.
* Linux / Steam Deck: Restringe ambientes Linux desktop utilizando Proton padrão
camadas devido a chamadas de kernel estritas. Existem exceções para o Steam Deck
ambientes com ajustes diretos de desenvolvedores de nível de jogo.
* Erros de exclusão mútua: A presença no nível do kernel de componentes ativos do sistema ACE
frequentemente provoca blocos de execução com frameworks anti-cheat rivais (como
Fácil Anti-Cheat) se ocorrerem ganchos sobrepostos.

------------------------------------------------------------------------------------------------------------------
4. INTEGRAÇÕES RECENTES E ATIVAS NOTÁVEIS (PC & MOBILE)
------------------------------------------------------------------------------------------------------------------
ACE é arquitetura de segurança padrão para propriedades e parceiros Tencent:
* Arena Breakout: Infinito
* Delta Force
* Mecha BREAK
* Honra dos Reis
* Call of Duty: Móvel
* ARC Raiders
* Idade dos Impérios Móvel
* Duet Night Abyss

------------------------------------------------------------------------------------------------------------------
5.Guia de limpeza manual e residual
------------------------------------------------------------------------------------------------------------------
Erros de desinstalação podem deixar registros de driver do sistema ativo para trás no Windows
depois de remover um jogo. Use este guia completo para remover artefatos restantes:

PASSO A: Purgar Serviços Ativos
1. Execute Prompt de Comando (CMD) ou PowerShell Windows como administrador.
2. Execute o seguinte script sequencialmente para remover o registro do sistema:
sc stop ACE- GAME
sc excluir ACE-GAME
s stop ACE- BASE
sc excluir ACE- BASE
sc excluir "Serviço AntiCheatExpert"
sc excluir "Proteção AntiCheatExpert"

PASSO B: Limpando Remanescentes de Disco
1. Reinicie o PC para liberar ganchos em arquivos de driver ativos.
2. Navegue para `C:\Program Files' e apague permanentemente o diretório `AntiCheatExpert`.
3. Navegue para `C:\Windows\System32\drivers` e solte arquivos chamados `ACE-GAME.sys`
ou «ACCE-BASE.sys» na Lixeira.

Use o código com cuidado. Se você estiver encontrando um erro de sistema específico, falha de jogo, ou conflito de driver relacionado com ACE, me avise qual jogo você está jogando e seu sistema operacional para que eu possa fornecer etapas de solução de problemas personalizadas!