Válvula anti fraude README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

Valve Anti Cheat, também chamado de VAC, é o sistema Valve para proteger servidores VAC protegidos no Steam. Ele é projetado para detectar software de fraude e modificações não autorizadas que dão aos jogadores uma vantagem injusta em jogos suportados.

Desenho geral

VAC está intimamente ligado ao Steam, servidores de jogos e jogos protegidos pela Valve. Quando um jogador se junta a um servidor VAC, o sistema pode verificar o ambiente do jogo e observar indicadores conhecidos de fraude. A aplicação do VAC é baseada na conta e geralmente se aplica ao jogo ou família de jogos onde a fraude foi detectada.

Abordagem de detecção

O VAC é amplamente entendido como um sistema de detecção automatizado. Em um nível conceitual seguro, ele pode identificar assinaturas conhecidas de fraude, arquivos de jogo alterados, módulos não autorizados, código suspeito carregado no jogo, e outros indicadores de que o processo do jogo não é limpo. VAC normalmente não publica detalhes técnicos, datas exatas de detecção, ou a fraude específica encontrada.

Proibições tardias

Uma característica fundamental da VAC é a aplicação tardia. Um jogador pode ser detectado antes da proibição aparecer. Este atraso ajuda a evitar que os desenvolvedores de fraudes aprendam imediatamente o que causou a detecção. Também permite à Valve agrupar detecções em ondas.

Confiança do servidor

Os servidores seguros VAC dependem do estado de proteção Steam e Valve. Se uma conta tem uma proibição VAC para um jogo protegido específico, essa conta não pode jogar em servidores protegidos VAC para esse jogo. Alguns jogos podem aplicar restrições mais amplas dependendo de como as regras de compartilhamento de jogos e Steam funcionam.

O que VAC não é

VAC não é um programa antivírus geral. Não se destina a limpar um computador, julgar cada processo, ou substituir ferramentas de segurança normais. Seu objetivo é proteger ambientes de jogo online específicos de modificações injustas conhecidas.

Falsos positivos e recursos

A Valve afirma que as proibições VAC são permanentes, excepto nos casos em que a Valve determina que uma proibição foi aplicada incorrectamente. O Suporte Steam normalmente não remove bans VAC manualmente. Esta política rigorosa destina-se a preservar a confiança na aplicação.

Conselhos do jogador

Não instale trapaças, treinadores, clientes rachados, ferramentas de peles suspeitas, editores de memória ou injetores em uma máquina usada para multiplayer protegido. Verifique os arquivos de jogo através do Steam após a modificação. Mantenha um único jogador modding separado do jogo protegido online.

[Plano geral do produto]
* Desenvolvedor: Valve Corporation
* Espectro de Sistema: VAC (Assinatura/Heurística) + VACNET (Modelo Comportamental IA)
* Arquitetura: Modo de usuário (Ring 3) Escudo de segurança [Não-Kernel]
* Filosofia Principal: "Atrasado Aplicação e Privacidade do Sistema." VAC opera
estritamente dentro dos limites do privilégio do usuário para evitar instabilidade OS, alavancando
ondas de proibição atrasadas para interromper ciclos de desenvolvimento de fraude e IA para detectar anomalias.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA E OPERAÇÕES DE FUNÇÃO
------------------------------------------------------------------------------------------------------------------
* Operação de Modo de Usuário: Diferente de drivers do kernel (por exemplo, Vanguard, EAAC) em execução em
Ring 0, VAC é executado inteiramente dentro do Modo de Usuário (Ring 3). Ele monitora o jogo
espaço de memória atribuído sem acesso ao kernel em todo o sistema.
* Componentes centrais locais: Integrado diretamente no oleoduto cliente Steam:
- Serviço Steam: Lida com a inicialização de fundo ("SteamService.exe").
- Active Scanning DLLs: Módulos dinâmicos injetados diretamente no processo do jogo
espaço de alocação de memória virtual durante uma sessão de matchmaking ativa.
* Limite de vida: VAC carrega em memória apenas quando se conecta a um seguro
servidor (marcado com o logotipo do escudo VAC) e descarrega ao desconectar. Sai.
nenhum serviço de fundo em execução ou drivers ativos quando o Steam ou o jogo estiver fechado.

------------------------------------------------------------------------------------------------------------------
2. MATRIXA DE SEGURANÇA E ANTI-EXPLOITAÇÃO
------------------------------------------------------------------------------------------------------------------
Válvula impõe segurança através de uma arquitetura em camadas combinando memória do lado do cliente
scans com aprendizado de máquina do lado do servidor:

* Cryptographic Memory Scanning: Verifica continuamente a RAM ativa do cliente do jogo
espaço, mapeamento de conjuntos de memória de execução para identificar terceiros não aprovados internos
ou injetores de código externos.
* Assinatura executável Blacklisting: Acompanha processos em execução contra uma lista dinâmica
de software de fraude conhecido. Quando ocorre uma correspondência de assinatura conhecida, a conta é
sinalizado para uma restrição atrasada.
* VACNet (AI Behavioral Engine): Uma extensa rede de aprendizagem profunda do lado do servidor.
Em vez de procurar por arquivos de software locais, VACNet processa milhares de dados
pontos por segundo (como movimento angular de retículos, mudanças na câmara e bala)
trajetórias) para capturar instantaneamente impossible aimbot ou spinbot movimentos.
* Fator de confiança Ecossistema: Avalia metadados da conta (incluindo a idade da conta, total
horas de jogo, status de guarda a vapor, histórico de relatórios e números de telefone ligados) para
Segregar perfis suspeitos em conjuntos separados.
* Hardware Biometric Linking: Liga identificadores permanentes de hardware (HWID) e telefone
números entre contas. Uma infração grave em cascatas de um perfil para proibir tudo
contas que partilham marcadores de verificação idênticos.

------------------------------------------------------------------------------------------------------------------
3. COMPATIBILIDADE UNIVERSAL E VANTAGENS CRUSS-PLATFORM
------------------------------------------------------------------------------------------------------------------
* Suporte ao Deck Nativo do Linux & Steam: Porque evita o nível restritivo do kernel
Drivers Windows, VAC funciona perfeitamente em arquiteturas Linux e Valve's
Camadas de tradução de prótons, fornecendo segurança padrão no Steam Deck.
* Estabilidade absoluta do sistema: Opera sem o risco de causar o sistema operacional
quebras (BSODs), conflitos de hardware, ou problemas de desempenho de leitura/escrita de armazenamento.
* Exclusão de terceiros: sinaliza proactivamente software que altera páginas de execução de código,
tais como injetores DirectX personalizados, trocadores de pele mais antigos, ou desempenho não verificado
sobrepõe esse gancho diretamente na linha visual do jogo.

------------------------------------------------------------------------------------------------------------------
4. TÍTULOS NOTÍVEIS QUE FORÇAM O VALVE ANTI-CHEAT
------------------------------------------------------------------------------------------------------------------
VAC protege o ecossistema de primeira parte da Valve juntamente com centenas de propriedades Steam licenciadas:
* Contra-Strike 2 (CS2)
* Dota 2
* Fortaleza da Equipe 2 (TF2)
* Esquerda 4 Morto / esquerda 4 Morto 2
* Portal 2 (Componentes Multiplayer)
* Rust (Utiliza VAC ao lado de Easy Anti-Cheat)
* Morto por luz do dia (Utiliza VAC ao lado de Easy Anti-Cheat)

------------------------------------------------------------------------------------------------------------------
5. MANUTENÇÃO, RESOLUÇÃO DO TEMPO, E FIXAS MANUAIS
------------------------------------------------------------------------------------------------------------------
Corrupção de arquivos locais, direitos de serviço Steam quebrados ou conflitos de software frequentemente
acionar o erro clássico "Um problema com seu computador está bloqueando o sistema VAC".
Siga estes passos precisos para restaurar loops de validação:

PASSO A: Forçar o Re-Registro do Serviço Steam
1. Saia completamente do cliente de desktop Steam.
2. Abra o menu Iniciar do Windows, digite "cmd", clique com o botão direito e escolha "Execute como Administrador".
3. Digite o caminho exato para o diretório de instalação do Steam seguido pela bandeira de reparo:
"C:\Program Files (x86)\Steam\bin\SteamService.exe" /repair
4. Espere a linha de comando para completar, em seguida, reiniciar o computador.

PASSO B: Expurgar Local DLL Cache & Verificar Arquivos de Jogo
1. Abra a Biblioteca Steam -> Clique com o botão direito do mouse no jogo afetado -> Selecione "Propriedades".
2. Navegue para "Arquivos Instalados" e clique em "Verificar a integridade dos arquivos de jogo".
3. Isso força o Steam a verificar todos os segmentos de execução, limpando o tempo de execução corrompido
DLLs e baixar componentes limpos e frescos.

PASSO C: Erradicar ganchos de software em conflito
1. O VAC bloqueará ativamente a conectividade se capturar aplicativos não verificados que alteram a memória.
2. Desactivar temporariamente ou desinstalar CCleaner, IObit Start Menu software, Cheat Engine,
ou remappers periféricos de nível de kernel personalizados antes de lançar um jogo protegido por VAC.
========================================================================================