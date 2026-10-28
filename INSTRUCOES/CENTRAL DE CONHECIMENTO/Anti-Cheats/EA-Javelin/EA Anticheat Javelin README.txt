EA Antiqueat ou Javelin

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

EA anticheat é Electronic Arts em casa PC tecnologia anti fraude. É usado em jogos selecionados da EA para proteger a integridade competitiva, especialmente onde fraudes podem afetar o jogo classificado, a economia e a justiça online.

Desenho geral

A EA anticheat combina um componente de cliente protegido, proteção de sistema de baixo nível para certos jogos, integração de jogos, telemetria lateral do servidor e avaliação da equipe de segurança da EA. Ele é construído para começar com jogos protegidos da EA e verificar se o ambiente de jogo é confiável.

Razão do nível do Kernel

A EA explicou que muitas fraudes modernas de PC operam a nível do kernel. Se um trapaceiro tem acesso mais profundo do que o jogo ou o anti-fraude, ele pode esconder adulteração de software comum. A EA anticheat usa proteção de nível de kernel para jogos onde a EA acredita que é necessário um acesso mais forte.

O que ele vê

Em um nível alto seguro, EA anticheat procura tentativas de interagir com ou alterar jogos protegidos EA. Isso pode incluir processos suspeitos, drivers, adulteração de memória, módulos não autorizados, depuração, modificação de arquivos e comunicação anormal com o jogo. A EA diz que o foco é proteção anti fraude em vez de atividade pessoal não relacionada.

Tratamento dos dados

A EA afirmou que a privacidade é uma preocupação e que as informações coletadas são limitadas ao que é necessário para fins anti fraude. O hashing pode ser utilizado para identificadores de modo que os valores originais não precisem ser armazenados em forma simples. Os jogadores ainda devem tratá-lo como poderoso software de segurança e ler os termos de privacidade da EA.

Desinstalar o comportamento

A EA afirmou que, se todos os jogos da EA que requerem antiqueat forem removidos, o antiqueat da EA também pode ser removido, e também pode ser desinstalado manualmente. Jogos que exigem que ele não executará modos online protegidos até que seja reinstalado.

Execução

A EA pode bloquear o lançamento, impedir o jogo online, remover os jogadores de sessões, contas de bandeira, proibições de emissão ou usar a investigação manual. Alguns novos títulos da EA também podem exigir recursos de segurança da plataforma, como o Secure Boot.

Conselhos do jogador

Mantenha as configurações de segurança Secure Boot e Windows no estado necessário para o jogo, evite drivers não assinados e sobreposições suspeitas e use suporte oficial da EA se o serviço falhar. Não use ferramentas de desbloqueio de terceiros, ferramentas de moedas, treinadores, spoofers ou editores de memória.

VISÃO GERAL DO PRODUTO]
* Desenvolvedor: Electronic Arts (EA)
(Engenharia segura de produtos e resposta anti-calor)
* Codinome/Identidade alternativa: EA Javelin Anti-Cheat
* Arquitetura: Kernel-Level (Ring 0) Solução de Segurança + DRM Anti-Tamper
* Método de Distribuição: Controlador de fundo proprietário ligado ao aplicativo EA / Steam
* Missão Principal: Prevenção direta de injeção de código de jogo de nível de sistema, RAM
modificação e macroexploração periférica.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA E FOTPRINT OPERACIONAL
------------------------------------------------------------------------------------------------------------------
* Modo Kernel (Ring 0): Opera nativamente no mais alto nível de privilégio de hardware
nas janelas. Atua como um driver de dispositivo especializado encarregado de auditoria do
Sistema operativo para vectores de injecção de código externo.
* Componentes ativos: Registra duas estruturas de sistema persistentes distintas:
- Diretório local: `C:\Program Files\EA\AC`
- Instalador primário: `EAAntiCheat. Installer.exe»
- Dependências de tempo de execução: `EAAntiCheat.GameServicesLauncher.exe`
* Limite de vida: Oficialmente funciona exclusivamente quando um jogo protegido pela EAAC
está a executar. Quando o executável de jogo correspondente desliga,
o condutor liberta os ganchos do sistema e entra num estado de sono completamente dormente.

------------------------------------------------------------------------------------------------------------------
2. CAPACIDADES DE SEGURANÇA & MITIGAÇÃO
------------------------------------------------------------------------------------------------------------------
* Anti-Tamper Layer: Características apertadas, compilação nativa dentro do binário do jogo.
Duplica-se como um elemento online Digital Rights Management (DRM) para parar de rachar offline.
* Integridade assistida por hardware: Utiliza biometria de hardware e HWID complexo (Hardware
Mecanismos de geração de identificadores para isolar permanentemente perfis de máquinas maliciosos.
* Processo Sandboxing: sinaliza proactivamente software de terceiros tentando manipular
espaço de memória do jogo, cobrindo ferramentas como motores de fraude, injetores de código,
e sobreposição de injetores.
* Filtragem periférica: Detecta ativamente ferramentas de virtualização de entrada não verificadas,
macros de hardware e modificações de entrada tentando simular ações humanas.

------------------------------------------------------------------------------------------------------------------
3. PARADOXES DE COMPATIBILIDADE E MONTANTES DE EXPANSÃO
------------------------------------------------------------------------------------------------------------------
* Linux & Steam Deck Bloqueado: Porque o sistema espera o kernel Ring 0 especializado
privilégios nativos no Windows, jogos implantados com EAAC completamente padrão de bloco
camadas de tradução de compatibilidade como o Linux Proton da Valve.
* Escala de Plataforma: Expandida explicitamente pela equipe SPEAR para estabelecer arquitetura nativa
para ambientes ARM64 Windows, combinando configurações de hardware mais recentes.
* Exclusão mútua de software: EAAC pode desencadear falsos positivos ou causar lançamento inesperado
falha se ele entrar em conflito com software de terceiros, como reWASD, DS4Windows,
ou software anti-fraude de terceiros (como Faceit).

------------------------------------------------------------------------------------------------------------------
4. TÍTULOS NOTÍVEIS QUE REFORÇAM A EA ANTI-CHEAT
------------------------------------------------------------------------------------------------------------------
A EA transferiu suas principais propriedades competitivas, multiplayer e esportivas para a EAAC:
* Battlefield 6
* Battlefield 2042
* Battlefield 1 / Battlefield V (atualizações Legacy)
* Série EA SPORTS FC (FC 24, FC 25, etc.)
* Plantas vs. Zombies: Guerra do Jardim 2
* Apex Legends (Migrações Graduais de Infraestrutura)
* Madden série NFL

------------------------------------------------------------------------------------------------------------------
5.Guia de limpeza manual e residual
------------------------------------------------------------------------------------------------------------------
Se você desinstalar um jogo, mas os componentes EA Anti-Cheat permanecem em seu sistema,
ou se um instalador danificado impedir um jogo de lançar, siga este manual completo
Guia de remoção:

PASSO A: Use o Instalador Oficial Independente
1. Abra o Windows Explorer e navegue para: `C:\Program Files\EA\AC`
2. Botão direito do mouse `EAAntiCheat. Installer.exe` e selecione "Executar como Administrador".
3. Clique na caixa drop-down, selecione um jogo específico para remover seus arquivos, ou clique
"Desinstalar tudo" no canto superior para remover totalmente a EAAC.

PASSO B: Terminação manual do serviço PowerShell (se preso)
1. Clique com o botão direito do mouse no menu Iniciar Windows e selecione "Terminal (Admin)" ou "PowerShell (Admin)".
2. Execute as seguintes linhas de comando para parar quaisquer tarefas de fundo persistentes:
sc stop EAntiCheatService
sc delete EAntiCheatService

PASSO C: Purgar as Pegadas dos Ficheiros
1. Reinicie o PC para garantir que todas as fechaduras abertas do driver são totalmente liberadas.
2. Navegue para `C:\Program Files\EA` e apague permanentemente toda a pasta `AC`.

[Plano geral do produto]
* Desenvolvedor: Electronic Arts (EA) Internal Security Engineering Team
* Classificação principal: Kernel-Level (Ring 0) Solução de segurança e anti-Tamper DRM
* Método de Distribuição: Motorista de fundo interno ligado ao aplicativo EA / Steam
* Missão Core: Prevenção direta de injeção de código de jogo de nível de sistema, memória
adulteração e macroexploração periférica nas franquias da EA.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA TÉCNICA E FOTPRINT OPERACIONAL
------------------------------------------------------------------------------------------------------------------
* Kernel Mode Privilege: Opera nativamente no mais alto nível de privilégio de hardware
no Windows (Ring 0). Atua como um driver de dispositivo especializado
auditoria do sistema operacional para vetores de execução de código não autorizados.
* Componentes ativos: Registra estruturas persistentes do sistema em sua unidade:
- Diretório base: `C:\Arquivos de Programa\EA\AC`
- Instalador primário: `EAAntiCheat. Installer.exe»
- Identificadores de serviço: Funciona sob `EAAntiCheatService`
* Limite de ciclo de vida: Funções como uma demanda-iniciar anti-fraude. Não tem.
carregar um driver de fundo persistente durante sua sequência inicial de inicialização do Windows.
Em vez disso, carrega quando um jogo protegido lança e entra em um completamente dormente
estado de sono quando o cliente do jogo sai em segurança.
* Requisitos mínimos: Requer Windows 10 20H1 (versão 10.0.19041) ou mais recente.

------------------------------------------------------------------------------------------------------------------
2. CAPACIDADES DE SEGURANÇA & MITIGAÇÃO
------------------------------------------------------------------------------------------------------------------
* Integridade de inicialização assistida por hardware: exige que UEFI Secure Boot e TPM 2.0
ser habilitado na BIOS em sistemas operacionais modernos. Isto permite que o Javelin
aproveitar o Windows para verificar que nenhum controlador comprometido carrega antes do jogo.
* Anti-Tamper Core: Apresenta uma matriz de compilação apertada tecida diretamente no jogo
binário. Ele serve como um componente DRM de dupla finalidade para bloquear a fissuração offline
enquanto monitora o espaço de memória ao vivo para ganchos de código ou injetores de fraude.
* Motor de Filtragem Periférica: Actively visa o uso de entrada não aprovada
software de virtualização e periféricos de "busca de hardware" (como o Cronus Zen)
que tentam converter entradas de mouse/teclado para simular controller aim assist.
* Telemetria Ecossistêmica: Feeds into EA's centralized database tracking milhões de PC
sessões de jogos. As atualizações são empurradas dinamicamente até as camadas do cliente para bloquear
centenas de programas únicos de fraude listados na lista negra globalmente.

------------------------------------------------------------------------------------------------------------------
3. ECOSISTEMA DEPLOYMENT & ECOSSISTEMA ROSTE
------------------------------------------------------------------------------------------------------------------
O dardo substituiu sistematicamente frameworks de terceiros mais antigos para unificar segurança
no competitivo catálogo multiplayer, esportes e serviços ao vivo da EA:
* Battlefield 6 (integração de lançamento principal)
* Battlefield 2042 / Battlefield V / Battlefield 1 (atualizações da infraestrutura Legacy)
* Série EA SPORTS FC (FC 24, FC 25, FC 26, etc.)
* Madden série NFL

------------------------------------------------------------------------------------------------------------------
4. DISCRIPÂNCIAS DE COMPATIBILIDADE E PORTO DE ARQUITETURA MODERNA
------------------------------------------------------------------------------------------------------------------
* Software Blocos de Exclusão Mútua: Porque auditorias Javelin Anel 0 atender pedidos,
pode desencadear falsos positivos ou falhas de lançamento ao encontrar controladores virtuais,
monitores de sistema desatualizados, interfaces personalizadas de controle de ventilador, ou sobreposição anti-barato
software (como reWASD, DS4Windows, Daemon Tools ou Faceit).
* Windows on Arm (ARM64) Suporte: Extensões de driver nativos são ativamente projetadas
para trazer Javelin em conformidade com as modernas arquiteturas de PC baseadas em ARM64.
* Linux & Proton Strategy Shift: Enquanto historicamente restritivo para ambientes de desktop Windows,
roadmaps de desenvolvimento delineiam explicitamente pipelines de engenharia para construir camadas de compatibilidade
para as camadas de tradução de Próton do Linux e da Valve para suportar o Steam Deck e o crescimento manual.

------------------------------------------------------------------------------------------------------------------
5. MANUTENÇÃO, REPARAÇÃO DO TEMPO E GUIA DE PURGAÇÃO MANUAL
------------------------------------------------------------------------------------------------------------------
Assinaturas digitais corrompidas, conflitos de cache locais ou falhas de atualização dinâmica
frequentemente se manifestam como Erro 95 (configuração inaceitável) ou Erro 115 (tempo limite / incapaz
a atualizar). Use estas sequências exatas para reparar ou limpar artefatos:

PASSO A: Use o utilitário de reparo de serviço integrado
1. Navegue diretamente para seus arquivos locais Javelin: `C:\Program Files\EA\AC`.
2. Botão direito do mouse `EAAntiCheat. Installer.exe` e escolha "Executar como Administrador".
3. Selecione seu jogo de destino no menu suspenso e clique em "Reparar".
4. Em alternativa, use o aplicativo EA: Clique nos três pontos na telha do jogo -> Selecione "Reparar".

PASSO B: Limpeza de High Privilege PowerShell (se o serviço for Hung)
1. Clique com o botão direito do mouse no menu Iniciar do Windows e abra "Terminal (Admin)" ou "PowerShell (Admin)".
2. Execute os seguintes comandos de terminal para limpar explicitamente as configurações de serviço parado:
sc stop EAntiCheatService
sc delete EAntiCheatService

PASSO C: Limpar disco completo e regras de exclusão
1. Reinicie o PC inteiramente para garantir qualquer restante memória de liberação de ganchos de hardware.
2. Abra o Windows Explorer, vá para `C:\Program Files\EA', e excluir permanentemente a pasta `AC'.
3. Para mitigar agressivo antivírus falso positivo bloqueando o jogo lança, adicione uma exclusão de arquivo
regra visando a pasta inteira `C:\Program Files\EA` dentro do seu Windows Defender ou
suite de software antivírus de terceiros.
========================================================================================