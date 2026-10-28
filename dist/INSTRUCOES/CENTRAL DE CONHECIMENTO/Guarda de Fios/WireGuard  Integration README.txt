GUIA DE INTEGRAÇÃO WIREGUARD
Conectando WireGuard ao seu aplicativo VPN de desktop autônomo personalizado
==================================================================================

OBJETIVO
--------
Este guia explica, em linguagem simples, como fazer seu próprio desktop VPN
aplicação usar WireGuard como seu motor VPN.

Pense em sua aplicação como o "painel de controle" e WireGuard como o
"motor" que realmente cria o túnel VPN.

Arquitetura:

+--------------------------------------------------+
Seu APP VPN de desktop personalizado
□ (Botões, Interface, Estado)
+--------------------------------------------------+
□
v
+--------------------------------------------------+
Motor de guarda de fios
* (Cria o Túnel VPN) *
+--------------------------------------------------+
□
v
+--------------------------------------------------+
Conexão à Internet
+--------------------------------------------------+


SECÇÃO 1 - COMO FUNCIONA WIREGUARD
--------------------
O WireGuard em si não fornece uma interface chique.

O trabalho do WireGuard é:

1. Leia um arquivo de configuração (.conf)
2. Criar um túnel criptografado
3. Rota tráfego de rede através do túnel
4. Desconectar quando solicitado

Sua aplicação simplesmente diz ao WireGuard o que fazer.


SECÇÃO 2 - COISAS DE QUE PRECISA
----------------------------
Vai precisar de:

1. Windows PC
2. Python instalado
3. WireGuard para Windows instalado
4. Seu aplicativo de desktop personalizado
5. Um ou mais arquivos de configuração VPN (.conf)

Exemplo:

configs/
proton.conf
servidor1.conf
servidor2.conf


SECÇÃO 3 - WIREGUARD INSTALADOR
----------------------------------------------------------------
1. Baixe WireGuard para Windows.
2. Instale-o normalmente.
3. Após a instalação, WireGuard irá instalar:

- Serviço de guarda de fios
- Motorista do túnel
- Adaptador de rede
- wireguard.exe

O WireGuard normalmente instala em:

Arquivos C:\Program\WireGuard\


SECÇÃO 4 - COMO A SUA APP DEVE SER PROJECTADA
---------------------------------------------

Seu aplicativo deve ter botões semelhantes a estes:

------------------------------------------------------------------------------------
[ Importar Configuração ]
[ Conectar ]
[ Desconectar ]
[ Status ]
[ Atualizar ]
[ Diagnósticos ]
------------------------------------------------------------------------------------

Características recomendadas:

• Importar perfis VPN
• Conectar
• Desconectar
• Exibir o status da conexão
• Mostrar o nome do túnel
• Mostrar o endereço IP atual
• Exibir estatísticas de transferência
• Mensagens de erro
• Janela de registo


SECÇÃO 5 - CRIAR UM FOLDER DE CONFIGO
-------------------------------------------------------------------

Dentro de sua pasta de aplicativos:

MyVPN/
□
MyVPN.exe
Configura/
(em milhões de euros)
Activos/

A pasta configura armazena seus perfis VPN.

Exemplo:

configs/
HomeVPN.conf
OfficeVPN.conf
GamingVPN.conf


SECÇÃO 6 - FILOS DE CONFIGO DE IMPORTAÇÃO
------------------------------------------------------------------

Permitir ao usuário:

1. Pressione Importar Configuração
2. Selecione um arquivo .conf
3. Copie o arquivo para:

configs/

Exemplo:

configs/
proton-us.conf


SECÇÃO 7 - O QUE ESTÁ NÍVEL DE UM .CONF FILE
---------------------------------------

Um arquivo de configuração do WireGuard geralmente contém:

[Interface]
Chave Privada=
Endereço=
DNS=

[Pier]
Chave Pública=
Permitido IPs=
Ponto final=

Seu aplicativo normalmente não edita esses valores.

Sua aplicação simplesmente carrega e usa o arquivo.


SECÇÃO 8 - RELATIVO A UM TUNEL
------------------------------------------------------------------

Sequência de ligação:

Cliques do usuário:
Ligar

Seu aplicativo:

Passo 1:
Localize o arquivo .conf selecionado.

Passo 2:
Verifica o ficheiro.

Passo 3:
Verificar WireGuard está instalado.

Passo 4:
Verificar os privilégios do administrador.

Passo 5:
Diz ao WireGuard para activar o túnel.

Passo 6:
Espere pela criação do túnel.

Passo 7:
Visualização:

ESTATUTO: CONEXO

Passo 8:
Mostrar o endereço IP público actual.


SECÇÃO 9 - DESCONHECIMENTO
----------------

Cliques do usuário:
Desligar

Seu aplicativo:

1. Diga ao WireGuard para parar o túnel
2. Espere para desligar
3. Atualizar interface

Visualização:

ESTATUTO: DESCONHECIDO


SECÇÃO 10 - DIREITOS ADMINISTRADORES
-----------------------------------------------------------------

Criar túneis VPN geralmente requer direitos de administrador.

Processo de inicialização recomendado:

1. Iniciar aplicação
2. Verificar privilégios de administrador
3. Se não elevado:
Pedido de elevação
4. Reinicie o aplicativo como Administrador

Sem permissões de administrador:

• A criação do túnel pode falhar
• Adaptadores de rede podem falhar
• Os serviços podem não iniciar


SECÇÃO 11 - VERIFYING WIREGUARD INSTALAÇÃO
-----------------------------------------------

Na inicialização seu aplicativo deve verificar:

1. A pasta WireGuard existe?

Arquivos C:\Programa\WireGuard

2. O wireguard.exe existe?

3. O serviço WireGuard está instalado?

4. O adaptador WireGuard está disponível?

5. A versão do WireGuard é detectável?

Visualização:

Estado do WireGuard:
⇩ Instalado
⇩ Serviço em execução
Adaptador disponível


SECÇÃO 12 - PANEL DE ESTATUTO SUGESTADO
-------------------------------------------------------------------

Estado da VPN:
----------------------------------------------------------------
Nome do túnel:
Estado da Ligação:
IP Público atual:
DNS:
Bytes Enviados:
Bytes Recebidos:
Tempo de Ligação:
----------------------------------------------------------------


SECÇÃO 13 - PAINEL DIAGNÓSTICO
---------------------

Diagnósticos recomendados:

⇩ Estado do administrador
文 Estado de instalação do WireGuard
文 Situação do serviço de túneis
‡ Validade do ficheiro de configuração
Teste de resolução de DNS
Teste de conectividade da Internet
Detecção pública de IP
⇩ Existência do adaptador
Estatísticas do túnel

Mostrar todos os resultados em linguagem simples.


SECÇÃO 14 - ERRO SEGURO
----------------------------------------------------------------

Mensagens de exemplo:

ERRO:
O WireGuard não está instalado.

ERRO:
Falta o arquivo de configuração.

ERRO:
Não foi possível iniciar o túnel.

ERRO:
Privilégios de administrador necessários.

ERRO:
Nenhuma ligação à Internet detectada.

Explique sempre problemas em linguagem simples.


SECÇÃO 15 - LOG FILES
----------------------

Criar:

logs/

Exemplo:

logs/
vpn.log

Registo:

Hora
Nome do túnel
Conectar eventos
Desligar eventos
Erros
Avisos
Diagnósticos

Os logs facilitam a resolução de problemas.


SECÇÃO 16 - FLORES RECOMENDADOS DE PEDIDO
---------------------------------------------------------

Início da Aplicação
□
V
Verificar os Direitos do Administrador
□
V
Verificar a Instalação do WireGuard
□
V
Carregar configurações
□
V
Interface de Visualização
□
V
Perfil da Seleção do Usuário
□
V
Ligar
□
V
Verificar a Correção do Túnel
□
V
Mostrar o Estado Ligado
□
V
Desligar
□
V
Voltar ao Estado Inativo


SECÇÃO 17 - CARACTERÍSTICAS A CONSIDERAR A REALIZAÇÃO
---------------------------------------------------------

Características básicas:
⇩ Configuração da Importação
Conectar
Desconectar
Estado
文 Logs

Características avançadas:
⇩ Exposição pública de IP
Exibição de DNS
Estatísticas de transferências
‡ Reconectar automaticamente
文 Interruptor de desligamento
⇩ Temporizador de conexão
Suporte à bandeja do sistema
文 Lançar na inicialização
‡ Perfis múltiplos
Varredor diagnóstico
‡ Registos de exportação


SECÇÃO 18 - PRINCÍPIO DE DESIGNAÇÃO IMPORTANTE
---------------------------------------

Sua aplicação nunca deve tentar desabilitar manualmente:

• Adaptadores Ethernet
• Adaptadores Wi-Fi
• Serviços de rede
• Pilha TCP/IP do Windows

Deixe o WireGuard gerir o seu próprio túnel.

Sua aplicação deve funcionar principalmente como:

1. Um painel de controle
2. Um gerenciador de perfil
3. Uma utilidade diagnóstica
4. Um painel de monitoramento

O próprio WireGuard deve permanecer responsável pela criação e gestão do túnel VPN.


RESUMO FINAL
--------------

Seu aplicativo VPN personalizado
□
v
Importar os Ficheiros de Configuração
□
v
Verificar a Instalação do WireGuard
□
v
Verificar os Direitos do Administrador
□
v
Iniciar o Túnel Através do Guarda- Fios
□
v
Estado do monitor
□
v
Mostrar IP público e estatísticas
□
v
Desligar o Túnel
□
v
Salvar registros
