Denuvo Anti fraude README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

Denuvo Anti Cheat é um produto de segurança de jogo de Irdeto. É separado de Denuvo tecnologia anti adulteração, embora ambos vêm da mesma família de proteção de jogo mais ampla. Seu objetivo é ajudar os editores a detectar trapaças, bots e comportamentos injustos em jogos online.

Desenho geral

Denuvo Anti Cheat pode ser integrado ao cliente do jogo e backend do editor. Irdeto descreve a proteção do jogo como um serviço de ciclo de vida que pode ajudar a detectar batota, apoiar decisões do editor e fornecer dados sobre a atividade de batota.

Detecção comportamental

Denuvo tem promovido características comportamentais anti fraude. Detecção comportamental significa que o sistema pode olhar para padrões em jogabilidade ou atividade de conta, em vez de apenas procurar um arquivo de fraude conhecido. Exemplos em um nível seguro incluem padrões de reação impossíveis, repetição tipo bot, movimento anormal, e outliers estatísticos.

Camadas de cliente e servidor

Um design em camadas pode combinar verificações de integridade local do cliente com revisão de comportamento lateral do servidor. Verificações locais podem identificar adulteração em torno do jogo protegido. Verificações laterais do servidor podem identificar comportamentos que violam as regras, mesmo que o sinal do cliente esteja incompleto.

Visibilidade do editor

Irdeto enfatiza dar aos publicadores perspicácia na atividade de fraude. Isso pode incluir painéis, relatórios, categorias de telemetria e evidências que ajudam a editora a decidir se bloqueia, proíbe, investiga ou afina os sistemas de jogos.

Privacidade e desempenho

Os produtos Denuvo têm sido controversos entre os jogadores de PC, em parte porque uma forte proteção pode levantar preocupações de privacidade e desempenho. Uma interpretação segura é que os jogadores devem ler a divulgação do editor para o jogo específico porque cada integração pode diferir.

Execução

Possível aplicação inclui prevenir o jogo protegido, marcar contas, proibir, remoção de bots, ou revisão manual. O editor normalmente controla o jogador enfrentando a disciplina.

Conselhos do jogador

Instale a partir de fontes de jogo oficiais, evite ferramentas de fraude e bots, mantenha o jogo atualizado, e verifique a página da editora de jogos para detalhes atuais do componente Denuvo. Não confunda anti fraude com anti adulteração porque eles resolvem problemas relacionados, mas diferentes.

[Plano geral do produto]
* Nome: Denuvo Anti-Cheat (DAC) [Irdeto - irdeto.com/video-games]
* Desenvolvedor: Denuvo Software Solutions GmbH (Subsidiário do Irdeto)
* Arquitetura: Kernel-Level (Ring 0) Driver + Servidor-Side AI Diagnósticos
* Distinção-chave: NÃO é o mesmo que "Denuvo Anti-Tamper" (Anti-Piracy/DRM).
DAC especificamente bloqueia exploração no jogo (imbots, wallhacks) em vez
do que impedir o jogo de rachar.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA e pegada OPERACIONAL
------------------------------------------------------------------------------------------------------------------
* Integração do Kernel: Instala um serviço de driver Ring 0 para monitorar
Sistema operativo para manipulações de sistemas não autenticadas.
* Componentes ativos: Registra dois serviços principais do sistema no Windows:
- Driver Service: `Denuvo Anti-Cheat` (Validação de execução de execução de execução)
- Serviço de Atualização: `Denuvo Anti-Cheat Update Service` (implantação de fundos)
* Filosofia de Execução "Só Leitura": Ao contrário de frameworks invasivos que proativamente
bloquear software periférico de terceiros, DAC usa uma abordagem não-intrusiva.
Analisa e relata anomalias silenciosamente sem restringir não maliciosas
Características do sistema operativo.
* Limite de ciclo de vida: O driver do kernel começa *apenas * quando o cliente do jogo
lança e desliga completamente quando o processo host termina. Funciona
estritamente durante os modos multiplayer online/competitivo.

------------------------------------------------------------------------------------------------------------------
2. MATRIXA DE SEGURANÇA E ANTI-EXPLOITAÇÃO
------------------------------------------------------------------------------------------------------------------
* Endurecimento de Nível Binário: Integrado diretamente no binário compilado do jogo
durante as construções de produção. Funciona nativamente sem necessitar de programadores
para configurar SDKs manuais ou APIs complexas.
* Proteçãos Anti-Hipervisor: Impressiona ativamente o ambiente do sistema
contra fraudes avançadas de virtualização assistidas por hardware.
* Anti-Automation Engine: Usa máquina de aprendizagem do lado do servidor para analisar bruto
fluxos de entrada em tempo real. Ele sinaliza scripts, macros, bots complexos, e
dispositivos de fraude de hardware não autorizados.
* Hardware Biometrics: Implementa impressão digital de hardware criptográfico.
Isso rastreia e ancora infrações severas em perfis de desktop únicos para
Impedir que os jogadores proibidos evitem penalidades com contas alternativas.
* Compatibilidade Linux / Steam Deck: Construído com suporte nativo para Valve
Camada de prótons, permitindo compatibilidade no SteamOS e no Steam Deck.

------------------------------------------------------------------------------------------------------------------
3. COMPATIBILIDADE & REPERCUSSÕES DE SISTEMA
------------------------------------------------------------------------------------------------------------------
* Arm64 Arm64 Architecture Support: Inclui camadas de execução nativas para Arm64
Sistemas de janelas. O anti- cheat é executado nativamente no kernel enquanto o jogo
binário executa através da tradução de hardware x86-to-Arm64.
* Nenhum DRM Linkage: Pode ser implantado em componentes multiplayer independentemente de
se o editor opta por comprar o Denuvo Anti-Tamper restritivo
Camada de software.
* Zero-Write Pegada: Não executa ciclos de leitura/escrita de armazenamento agressivo,
desmascarando mitos de longo prazo alegando que o software causa hardware físico
degradação em SSDs ou HDDs.

------------------------------------------------------------------------------------------------------------------
4. REMOVAL, MANUTENÇÃO E MANUALIZAÇÃO
------------------------------------------------------------------------------------------------------------------
Se as rotinas de desinstalação falharem ou deixarem configurações de serviço dormente
no seu sistema, use a seguinte sequência de script manual para limpar todos os elementos:

PASSO A: Purgar os Serviços do Windows Registrados
1. Pressione a tecla do Windows, digite "cmd", e selecione "Execute como Administrador".
2. Colar e executar os seguintes comandos de terminal para completamente não registrar DAC:
sc stop "Denuvo Anti-Cheat"
sc apagar "Denuvo Anti-Cheat"
sc stop "Denuvo Anti-Cheat Update Service"
sc apagar "Denuvo Anti-Cheat Update Service"

PASSO B: Tirar os artefactos do sistema de arquivos
1. Abra aplicativos e recursos do Windows (`Configurações -> Apps -> Apps instalados`).
2. Localize e desinstale "Denuvo Anti-Cheat" se permanecer visível na lista.
3. Limpe o diretório do cliente do jogo para remover links dinâmicos obsoletos ou wrapper
módulos associados a instalações anteriores.