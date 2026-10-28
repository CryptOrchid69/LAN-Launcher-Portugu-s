README EQU8

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

EQU8 é uma solução anti fraude focada no cliente para jogos de PC online. Destina-se a ajudar estúdios a proteger jogos multiplayer de hackers, ferramentas de fraude e software injusto, dando aos desenvolvedores informações sobre eventos de segurança do jogador.

Desenho geral

O EQU8 está integrado ao cliente do jogo e ao processo de inicialização. Quando um jogo protegido começa, EQU8 verifica se seus componentes podem carregar, se o ambiente do jogo parece confiável, e se programas suspeitos ou comportamento adulterador estão presentes.

Foco no cliente

Um sistema focado no cliente observa o que acontece em torno do processo de jogo do jogador. Em um nível seguro, isso pode incluir interação de processo, adulteração de memória, módulos não autorizados, drivers suspeitos, assinaturas de fraude conhecidas, ferramentas de automação e tentativas de interferir com o próprio serviço anti fraude.

Informação do desenvolvedor

O EQU8 é descrito como fornecendo proteção e análise. Isso significa que um desenvolvedor pode receber relatórios sobre categorias de fraude, eventos suspeitos e erros do lado do jogador. Esses relatórios podem ajudar o estúdio a afinar regras, investigar incidentes e melhorar a compatibilidade.

Por que os assuntos leves

Alguns estúdios querem proteção anti fraude sem construir uma grande equipe de segurança interna. Um terceiro leve anti fraude pode fornecer uma camada base pronto feito. O tradeoff é que o estúdio ainda deve lidar com políticas comunitárias, apelos, e jogos específicos explore correções.

Compatibilidade

Como outras ferramentas de segurança, o EQU8 pode entrar em conflito com ferramentas de depuração, sobreposições, virtualização, drivers incomuns, macro utilitários e produtos antivírus. A compatibilidade pode diferir de um jogo protegido para outro.

Execução

O EQU8 pode suportar lançamento bloqueado, chutes de jogo, bandeiras de contas suspeitas ou banimentos de editores. O estúdio de jogos normalmente decide a política de execução final.

Conselhos do jogador

Mantenha o jogo atualizado, remova ferramentas relacionadas a fraude, evite editores de memória, evite pacotes de driver suspeitos e use o caminho oficial de suporte para erros. Nunca baixe arquivos anti fraude substituição de sites não oficiais.

[Plano geral do produto]
* Desenvolvedor: Int3 Software (adquirido / em parceria com AccelByte) [accelbyte.io]
* Arquitetura: Hybrid (Dynamic User-Mode Agent + On-Demand Kernel Driver)
* Filosofia chave: cliente-centrado, leve fronteira de segurança enfatizando
integridade da sessão, baixa sobrecarga do sistema e correlação de telemetria direta sobre
monitorização persistente dos antecedentes.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA & OPERAÇÃO DE SISTEMAS
------------------------------------------------------------------------------------------------------------------
* Execução On-Demand: EQU8 opera estritamente em um ciclo de vida ligado ao jogo.
Ele carrega exclusivamente quando o jogo host inicia e termina completamente tudo
tarefas do sistema e execução de fundo no momento em que o jogo sai.
* Numeração de Serviço Modular: Usa um esquema de sufixo dinâmico baseado na compilação
Versões (por exemplo, EQU8 39, EQU8 13). Regista temporariamente
dois mecanismos essenciais do sistema durante uma sessão de jogo ao vivo:
- Serviço de lançamento: denominado «EQU8 [Versão]» (por exemplo, «EQU8 36»)
- Controlador auxiliar do Kernel: chamado `EQU8 HELPER [Version].sys`
* Pegada de Processo: Lança um gerenciador de modo de usuário ofuscado ao lado do jogo
binário, normalmente rastreado como `agent.x64.equ8.exe` ou `antichaat.x64.equ8.exe’.

------------------------------------------------------------------------------------------------------------------
2. CAPACIDADES DE SEGURANÇA & MITIGAÇÃO
------------------------------------------------------------------------------------------------------------------
* Callbacks do sistema: O driver do kernel (`EQU8 HELPER *.sys`) configura um processo rigoroso
rotinas de criação e pré-operação lidar com callbacks através do kernel do Windows.
Isto intercepta manipulação de memória externa não autorizada.
* Bloqueio de injeção: Monitores ativos para eventos de análise dinâmica, interceptando
casos em que bibliotecas não autorizadas do Dynamic Link (DLLs) são forçadas a entrar no jogo
ou depuradores externos tentam anexar aos threads da aplicação.
* Arquivo envoltório & Configurações: Aproveita camadas de regras criptografadas localmente (como
`equ8.cfg` e `equ8 con.json`) para estabelecer parâmetros de validação do sistema de arquivos.
* AccelByte Telemetry Sync: Alimenta anomalias de execução em tempo real diretamente na infraestrutura
Infra-estrutura de nuvem. Em vez de avaliar a traição num silo completo,
cruza as referências de impressões digitais de hardware, perfis de SO e traços de conta para marcar
atores recorrentes maliciosos.

------------------------------------------------------------------------------------------------------------------
3. COMPATIBILIDADE & REPERCUSSÕES DE SISTEMA
------------------------------------------------------------------------------------------------------------------
* Agilidade do motor: Implantado como um invólucro leve fortemente favorecido por automatizado
Implementos de vapor e arquiteturas modulares de motores (como Unity e Unreal Engine).
* Windows Testing Block: EQU8 bloqueia a execução estritamente se o host OS for inicializado
"Modo de Teste do Windows" (modo de sinalização de testes), uma vez que este ambiente permite não verificado,
drivers de kernel feitos pelo usuário para comprometer as salvaguardas de memória.
* Blocos de Exclusão Mútua: Porque registra manipuladores de IRP de baixo nível durante o jogo
lança, frequentemente colide com anti-quedas persistentes altamente agressivas.
Ambientes de execução ativos como o Riot Vanguard ou instâncias de depuração ativa de
O Cheat Engine frequentemente aciona falhas de validação imediatas.

------------------------------------------------------------------------------------------------------------------
4. TÍTULOS NOTÍVEIS QUE REFORÇAM O EQU8 ANTI-CHEAT
------------------------------------------------------------------------------------------------------------------
O EQU8 tem historicamente protegido vários títulos de multijogador competitivo e treinamento de objetivos:
* Splitgate
* Batalhas totalmente precisas (TABG)
* KovaaK's (Aim Trainer)
* Diabótico (Implementação de Legacy)
* Universo duplo

------------------------------------------------------------------------------------------------------------------
5. ELIMINAÇÃO, REPARAÇÃO E LIMPEZA MANUAL RESIDUAL
------------------------------------------------------------------------------------------------------------------
Se uma compilação integrada não deixar cair completamente a sua configuração de serviço temporário,
ou se os erros de assinatura ("Acesso é Negado 0005") pararem a inicialização do jogo, siga
Este protocolo de depuração manual:

PASSO A: Purgar o registro ativo do serviço do Windows
1. Pressione a tecla do Windows, digite "cmd", e selecione "Execute como Administrador".
2. Execute os seguintes comandos de terminal para remover os serviços de compilação parada (substituir
o sufixo de número com o código de versão exato que seu prompt de erro exibe:
sc parar EQU8  36
sc apagar EQU8  36
sc parar EQU8  39
sc apagar EQU8  39

PASSO B: Reconstruir o Cliente JSON Infra-estruturas
1. Navegue diretamente para os arquivos de instalação locais do seu jogo através do Steam.
2. Pesquise o diretório raiz e delete `equ8 con.json` junto com `equ8-launcher.exe`.
3. Abra o Steam, clique com o botão direito do mouse no jogo -> Propriedades -> Arquivos Instalados -> Clique
"Verificar a integridade dos arquivos de jogo" para forçar um re-download limpo e não corrompido.

PASSO C: Drivers de Kernel Residual Strip
1. Reinicie o PC para garantir que quaisquer bloqueios de thread abertos em objetos do driver são limpos.
2. Abra o Windows Explorer e navegue para: `C:\Windows\System32\drivers`
3. Localize quaisquer arquivos explicitamente prefixados com `EQU8 HELPER ` (por exemplo, `EQU8 HELPER 36.sys`)
e excluí-los permanentemente