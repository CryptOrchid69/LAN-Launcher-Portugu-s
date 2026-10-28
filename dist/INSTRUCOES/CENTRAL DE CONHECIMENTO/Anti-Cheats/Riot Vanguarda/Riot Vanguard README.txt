README de Vanguarda de Riot

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

Riot Vanguard é o sistema anti-trapaça personalizado da Riot Games usado para títulos competitivos como VALORANT e League of Legends no PC. Ele é projetado para proteger a integridade competitiva em jogos onde uma pequena vantagem injusta pode arruinar o jogo classificado.

Desenho geral

A Vanguard usa uma aplicação cliente, um driver de modo kernel, validação do lado do servidor, execução da conta Riot, análise de telemetria e pesquisa de segurança ativa. O sistema verifica se a máquina está em um estado confiável antes de permitir o jogo protegido. Ele também pode impedir o jogo de lançar se as condições de segurança necessárias não são cumpridas.

Protecção do nível de arranque

Vanguard é conhecido por carregar um driver no início do processo de inicialização do Windows. O objetivo é reduzir a chance de que uma fraude pode começar primeiro, se esconder, e depois manipular o jogo antes que o anti fraude é ativo. Este design é poderoso, mas é também por isso que a Vanguard recebe atenção de jogadores que estão preocupados com privacidade e controle do sistema.

O que ele observa em um nível seguro

A Vanguard foca na manipulação de jogos de Riot. Ele pode verificar por drivers suspeitos, acesso não autorizado à memória, adulteração de processos de jogo, indicadores de depuração, padrões de trapaça assistidos por hardware, comportamento de entrada anormal e estados do sistema que enfraquecem a confiança. Ele também usa dados do lado do servidor para detectar comportamentos que não correspondem ao jogo humano normal.

Confiança em hardware e firmware

As fraudes de alto nível modernas podem usar truques de hardware externo ou nível de firmware. A Vanguard confiou cada vez mais em sinais de segurança da plataforma, tais como Secure Boot, TPM, proteção IOMMU e requisitos de firmware de placa-mãe em certos contextos. Estas verificações tentam tornar mais difícil para dispositivos de fraude esconder fora do sistema operacional normal.

Análise lateral do servidor

O Riot combina segurança do cliente com análise de jogabilidade. Um jogador pode ser investigado por causa de padrões de mira impossíveis, tempo de reação anormal, comportamento incomum da conta, histórico de dispositivo suspeito, ou relatórios que correspondem à telemetria técnica. Revisão humana e detecção automatizada podem funcionar em conjunto.

Execução

A Vanguard pode bloquear o lançamento, exigir alterações de configuração do sistema, remover um jogador de uma partida, banir contas e aplicar uma ação mais forte contra a repetição ou trapaça ligada ao hardware. O Riot muitas vezes atualiza o Vanguard porque o desenvolvimento de fraudes muda rapidamente.

Conselhos do jogador

Manter Recursos de segurança do Windows habilitados, atualizar firmware da placa-mãe apenas do fabricante oficial, evitar ferramentas de fraude e drivers desconhecidos e usar o suporte oficial do Riot para erros. Não siga guias de internet que lhe dizem para enfraquecer as configurações de segurança apenas para executar ferramentas suspeitas.

[Plano geral do produto]
* Desenvolvedor: Riot Games Inc.
* Arquitetura: Nativo Kernel-Level (Ring 0 Boot Driver) + Cliente de Modo de Usuário
* Suporte à Plataforma: Windows 10 e Windows 11 (apenas nativo de 64 bits)
* Filosofia: "Profunda Prevenção e Exclusão Imediata". Opera como um
Embrulho de segurança altamente restritivo que lança no tempo de arranque do sistema para
isolar o espaço de memória antes de qualquer potencial explore drivers podem inicializar.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA & OPERAÇÃO DE SISTEMAS
------------------------------------------------------------------------------------------------------------------
* Integração de inicialização do sistema: Vanguard é executado como um driver de inicialização. Inicia-se em
a primeira fase do processo de arranque do sistema operativo (Ring 0) para garantir
linha de base segura antes que o software modo-usuário possa ser executado.
* Core System Process Components: Divide suas operações em duas camadas distintas:
- Controlador do Kernel: `vgk.sys` localizado dentro de `C:\Windows\System32\drivers`
- Cliente de Modo de Utilizador: `vgc.exe` a ficar sem `C:\Program Files\Riot Vanguard`
* Perfil de Serviços Ativos: Registra o serviço 'vgc' no Windows (`Riot Vanguard
Ícone de Notificação». Desactivar este serviço bloqueia o acesso aos jogos Riot.
* Limite de vida: O driver do kernel (`vgk.sys`) é executado constantemente em segundo plano
da inicialização do sistema. O cliente modo usuário (`vgc.exe`) pode ser fechado manualmente através do
bandeja do sistema, mas jogar títulos protegidos por Vanguard requer uma reinicialização completa do hardware
para restaurar ganchos de verificação do sistema.

------------------------------------------------------------------------------------------------------------------
2. MATRIXA DE SEGURANÇA E ANTI-EXPLOITAÇÃO
------------------------------------------------------------------------------------------------------------------
* Execução de Assinatura do Driver (DSE): Estritamente bloqueia vulnerável ou não patched
drivers de hardware de terceiros (explorações BYOVD) que podem permitir código malicioso
para manipular estruturas de jogo de nível de kernel.
* Rastreamento Biométrico de Hardware: Cria HWID único e persistente (Hardware Identifier)
Perfis baseados em metadados BIOS subjacentes. Isto impede os jogadores banidos de
utilizando contas alternativas na mesma máquina.
* Ato de desaparecimento (Instant Drop): instantaneamente desliga jogos multiplayer ao vivo
o milissegundo exato que um trapaceiro é marcado pela lógica de verificação do lado do servidor,
restaurando pontos de classificação para jogadores não afetados.
* Deep Virtualization Block: Utiliza ganchos de virtualização assistidos por hardware.
Activamente sinaliza ou termina o cliente se detectar hipervisores isolados,
sandboxes, ou configurações de hardware não verificadas tentando ocultar memória.

------------------------------------------------------------------------------------------------------------------
3. MANDATES E MONTANTES DE COMPATIBILIDADE
------------------------------------------------------------------------------------------------------------------
Para combater as façanhas avançadas de hardware, a Vanguard impõe BIOS e sistema rígidos
perfis de segurança:
* UEFI Secure Boot & TPM 2.0: requisito rígido absoluto sob Windows 11. O anti- fraude
recusar- se- á deixar o jogo lançar se o sistema detectar que estas configurações são ignoradas
ou desativado na BIOS.
* Linux, Wine, & Mac Total Exclusion: Vanguard bloqueia completamente a execução sob Linux,
Válvula Próton, Vinho ou macOS. Porque os sistemas operativos alternativos não podem replicar
Os requisitos exatos de verificação do kernel da Riot, estas plataformas estão completamente bloqueadas.
* Exclusão Mútua de Software Periférico: Agressivamente blacklists ou impede a inicialização
quando os conflitos de desenho ocorrem com softwares de terceiros específicos, tais como hardware personalizado
monitores, gerenciadores de sobreposição não verificados ou remappers macro.

------------------------------------------------------------------------------------------------------------------
4. TÍTULOS NOTÁVEIS QUE REFORÇAM O VANGUARDO RIOT
------------------------------------------------------------------------------------------------------------------
A Vanguard protege os principais títulos competitivos e táticos da Riot Games:
* VALORANT (Ambiente de lançamento padrão desde 2020)
* Liga das Lendas (Infraestrutura migrada globalmente na Primavera de 2024)
* Táticas de luta de equipes (TFT - Implantado ao lado da migração de clientes de desktop da Liga)

------------------------------------------------------------------------------------------------------------------
5. ELIMINAÇÃO, RESUBMISSÃO E MANUALIZAÇÃO DE SERVIÇO
------------------------------------------------------------------------------------------------------------------
Se um loop de patch Vanguard falhar, ou se um erro persistente de "Vanguard Not Inicialized"
ocorre, siga este guia de limpeza manual abrangente:

PASSO A: Use o motor de desinstalação oficial
1. Feche todos os processos ativos do cliente Riot.
2. Abra aplicativos e recursos do Windows (`Configurações -> Apps -> Apps instalados`).
3. Localize "Riot Vanguard" na lista, clique no ícone de opções e selecione "Desinstalar".

PASSO B: High-Privilege PowerShell Clean
1. Se o desinstalador padrão pendura, clique com o botão direito do mouse no menu Iniciar do Windows e selecione
"Terminal (Admin)" ou "PowerShell (Admin)".
2. Execute as seguintes linhas de comando para excluir manualmente os serviços subjacentes:
sc stop vgc
sc stop vgk
sc excluir vgc
sc excluir vgk

PASSO C: Expurgar artefatos de arquivo remanescentes
1. Reinicie o PC para desbloquear quaisquer arquivos de driver restantes na memória.
2. Abra o Windows Explorer e navegue para: `C:\Program Files'
3. Excluir o diretório `Riot Vanguard' inteiramente.
4. Navegue para `C:\Windows\System32\drivers` e apague permanentemente `vgk.sys`.
========================================================================================