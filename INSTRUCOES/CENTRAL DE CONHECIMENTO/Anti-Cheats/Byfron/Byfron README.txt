Byfron README

Objecto

Este documento é escrito para jogadores legítimos, proprietários de servidores, modders e desenvolvedores que querem entender a proteção de fair play em um nível conceitual seguro. Não inclui etapas de desvio, explorar detalhes, código de fraude, procedimentos de evasão, ou instruções para derrotar a proteção.

Byfron era uma empresa conhecida por anti trapaça e tecnologia resistente. Roblox adquiriu a Byfron, e sua tecnologia é comumente associada à proteção do cliente Roblox Hyperion. O nome ainda é usado por muitos jogadores ao discutir a proteção anti-exploração Roblox.

Desenho geral

Proteção estilo Byfron foca em tornar um cliente de jogo mais difícil de inspecionar, alterar, injetar ou controlar com ferramentas de exploração externa. O objetivo não é apenas encontrar uma fraude após sua execução, mas também fazer fluxos de trabalho de exploração comuns não confiáveis.

Endurecimento do cliente

Em um nível seguro, o endurecimento do cliente pode envolver verificações de integridade, antidepuração, proteção de memória, proteção de código, detecção de adulteração e verificação de interação suspeita com o processo protegido. Estes conceitos são comuns tanto em produtos anti fraude e anti adulteração.

Utilização numa plataforma

Para uma plataforma como Roblox, o endurecimento do cliente ajuda a proteger milhões de experiências diferentes de ferramentas de exploração comuns. Não substitui o bom design do servidor. Donos de plataformas e desenvolvedores de experiência compartilham responsabilidade.

Por que os detalhes são limitados

Anti batota e anti adulteração fornecedores raramente publicar detalhes de implementação profunda porque essa informação ajudaria a explorar desenvolvedores. O conhecimento público é, portanto, geralmente limitado a conceitos seguros, comportamento observado e declarações oficiais.

Limitações

Nenhuma proteção ao cliente é perfeita. Os atacantes podem se adaptar, então o sistema deve se atualizar com o tempo. A proteção do cliente também tem que evitar prejudicar jogadores normais, ferramentas de acessibilidade e fluxos de trabalho de desenvolvimento legítimos.

Conselhos de jogador e desenvolvedor

Os jogadores devem evitar explorar executores e clientes não oficiais. Os desenvolvedores devem projetar sistemas de autoridade do servidor, validar eventos remotos, limitar o comportamento suspeito e nunca confiar nos valores fornecidos pelo cliente para o estado importante do jogo.

[Plano geral do produto]
* Nome: Byfron Technologies (Adquirido pela Roblox Corporation)
* Flagship Produto: Hyperion
* Classificação principal: Software Anti-Tamper do lado do cliente e Escudo de Integridade
* Suporte à Plataforma: Windows (somente nativo de 64 bits)
* Filosofia: Prevenção da manipulação binária, engenharia reversa, e
depurando sobre heurísticas de comportamento pós-fato.

------------------------------------------------------------------------------------------------------------------
1. ARQUITETURA COMPLEMENTAR: ANTI-TAMPPER VS. ANTI-CHEAT TRADICIONAL
------------------------------------------------------------------------------------------------------------------
* Defesa de Modo de Usuário: Ao contrário das defesas do driver do kernel Ring 0 (por exemplo, Vanguard, ACE),
Hyperion opera fundamentalmente como um avançado User-Mode (Ring 3) embrulho anti-tamper.
* Endurecimento Binário: Envolve o executável do aplicativo alvo (`RobloxPlayerBeta.exe`)
em uma camada fortemente ofuscada, mutando padrões binários padrão para quebrar o tradicional
desmontadores e descompiladores (como IDA Pro ou Ghidra).
* Execução de 64 bits: Hyperion funciona exclusivamente em sistemas operacionais de 64 bits.
Os pontos de entrada legados de 32 bits foram totalmente depreciados para garantir um controlo uniforme sobre
x86-64 memória endereçando espaço.

------------------------------------------------------------------------------------------------------------------
2. Utilidades de proteção de linha e corrida
------------------------------------------------------------------------------------------------------------------
* Anti-Debugging & Hooking Vectors: Monitora continuamente estados de thread runtime.
Intercepta ativamente tentativas de software externo para conectar tempo de execução vital
endereços, injetar Bibliotecas de Link Dinâmico (DLLs), ou anexar depuradores.
* Verificação de integridade de código: periodicamente mapeia e verifica seções de código
dentro da memória do sistema. Se detectar alterações nos segmentos de texto ou modificações
de activos estáticos, desencadeia uma rescisão imediata do cliente.
* Advanced Virtual Machine Blocking: Implementa o hipervisor e a impressão digital do ambiente.
Tenta hospedar o cliente dentro de sandboxes isoladas ou máquinas virtuais padrão
Abortar frequentemente a terminação.
* Limite de compatibilidade do sistema operacional: Blocos explicitamente camadas de tradução de compatibilidade
como o vinho, incitando "o vinho não é suportado" erros para evitar o desvio de
ganchos de validação da máquina.

------------------------------------------------------------------------------------------------------------------
3. INTEGRAÇÃO DAS REDES E DOS SERVIÇOS
------------------------------------------------------------------------------------------------------------------
* Canais de telemetria compartilhados: alimenta registros internos de estado diretamente para o lado do servidor
lógica de validação, permitindo que servidores de jogos verifiquem a autenticidade do cliente.
* Sistemas Ban-Wave: Em vez de banir instantaneamente os atores detectados no local,
Hyperion rastreia metadados HWID (Hardware ID) e agrega infrações para
ondas de proibição sistemáticas atrasadas.
* Alt-Account Association: Registra marcadores estruturais do sistema para amarrar não autorizados
atividade em contas de gravação de volta para um ambiente de desktop pai único.

------------------------------------------------------------------------------------------------------------------
4. CONFORMIDADE DE INTEGRAÇÃO & FOTPRINT HISTÓRICO
------------------------------------------------------------------------------------------------------------------
* Early Adopters: Antes da aquisição corporativa completa, as camadas protetoras da Byfron
foram testados ao lado de soluções existentes em jogos como Apex Legends.
* Implantação Primária: Totalmente adquirido no final de 2022 pela Roblox Corporation; serve
como o limite estrutural de segurança do desktop para o cliente nativo do Windows.
* Gaps de plataforma: Não executa seu invólucro binário primário de endurecimento em dispositivos móveis
ecossistemas (iOS/Android), focando inteiramente na segurança do cliente desktop.

------------------------------------------------------------------------------------------------------------------
5. MANUTENÇÃO E RESOLVÊNCIA DO COMPORTAMENTO ANOMÁTICO
------------------------------------------------------------------------------------------------------------------
Porque o Hyperion é compilado dentro do invólucro da aplicação em si, ele não sai
drivers de fundo persistentes ou serviços distintos do Windows em execução quando o cliente do jogo
Fecha. Para limpar seus arquivos de cache transitórios ou resolver falhas:

PASSO A: Expurgar a Pegada do AppData
1. Pressione `Windows Key + R` para solicitar a janela Executar.
2. Digite `%localappdata%` e clique em OK.
3. Localize a pasta 'Roblox' e exclua-a inteiramente. Isto limpa completamente o cache
artefatos de memória anti-cheat, configurações de clientes e estados dinâmicos quebrados.

PASSO B: Limpeza de Registros (para HWID / Estados Presos)
1. Abra a janela Executar, digite `regedit` e execute como Administrador.
2. Navegue para: `HKEY CURRENT USER \Software'
3. Delete a pasta de registro de chaves `Roblox` para forçar o motor a reconstruir limpo,
Identificadores de clientes não contaminados no próximo ciclo de lançamento.
========================================================================================