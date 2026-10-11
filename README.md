# MyHUB MCP

Use as ferramentas de IA do [MyHUB.IA](https://myhub.ia.br/) direto no **Claude Desktop** e no **Claude Code**:
converse com GPT, Claude, Gemini, DeepSeek e outros modelos, use seus agentes, anexe arquivos, gere imagens
e vídeos, e consulte seu histórico e seus créditos, tudo de dentro do Claude.

> Projeto independente, sem vínculo com o MyHUB.IA nem com a Anthropic. Você precisa de uma conta ativa no MyHUB.IA.

## Instalação (Windows)

Abra o **PowerShell** (menu Iniciar → digite *PowerShell*; não precisa ser administrador) e cole:

```powershell
irm https://github.com/GabrielStange/myhub-mcp-dist/releases/latest/download/install.ps1 | iex
```

O instalador prepara tudo e abre um **assistente** que você navega com as setas, o espaço e o Enter:

```
  MyHUB MCP · configuração

━━ Passo 1/6 · Verificando o ambiente ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ✓ Windows 11
  ✓ acesso a myhub.ia.br
  ✓ Claude Desktop instalado
  ! Claude Code não encontrado
  ! GitHub CLI não encontrado (opcional: abre issues automaticamente)

━━ Passo 2/6 · Onde usar o MyHUB ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
? Em quais aplicativos o MyHUB deve aparecer?  (espaço marca, Enter confirma)
 » ● Claude Desktop (aplicativo)
   ● Claude Code (terminal)
```

1. **Ambiente:** verifica o Windows, a rede e os aplicativos.
2. **Onde usar:** Claude Desktop e/ou Claude Code. Se faltar algum, o assistente oferece instalar.
3. **Conta do MyHUB.IA:** abre o navegador para você entrar. A senha fica só no navegador.
4. **Preferências:** modelo padrão, qualidade das imagens e fuso horário.
5. **Relatório de problemas:** automático (com o GitHub CLI, que o assistente pode instalar), pelo navegador ou desligado.
6. **Painel e atalhos.**

Depois de você confirmar o resumo, ele conecta o MyHUB aos aplicativos, reinicia o Claude Desktop e confirma
que o servidor carregou.

Pré-requisitos: Windows 10/11 e uma conta no MyHUB.IA.

## Comando `myhub`

Em qualquer PowerShell aberto depois da instalação:

| Comando | Para quê |
|---|---|
| `myhub setup` | Refaz o assistente (as respostas anteriores vêm como padrão) |
| `myhub doctor` | Mostra o que está funcionando e o que falta (não gasta créditos) |
| `myhub login` | Entra de novo na conta do MyHUB.IA |
| `myhub site` | Abre o MyHUB.IA sem desconectar o Claude |
| `myhub painel` | Abre o painel de uso |
| `myhub config set default_model CLAUDE_OPUS_5_5` | Muda uma preferência (`myhub config list` mostra todas) |
| `myhub update` | Atualiza para a versão mais recente |
| `myhub uninstall` | Remove o MyHUB MCP |

## Como usar

No Claude Desktop ou no Claude Code (`claude` no terminal), peça em linguagem natural:

- *"Quantos créditos eu tenho no myhub?"*
- *"Pergunte ao Gemini 3.1 Pro pelo myhub: o que é OPC UA?"*
- *"Liste meus chats recentes no myhub e resuma o último."*
- *"Envie o arquivo relatorio.pdf ao Claude Opus 5.5 pelo myhub e peça os pontos principais."*
- *"Gere no myhub uma imagem de uma subestação ao pôr do sol."* (consome créditos)

Na primeira vez que cada ferramenta for usada, o Claude pede sua autorização.

No **Claude Desktop**, o MyHUB aparece em **Configurações → Desenvolvedor** e no menu de ferramentas da conversa.

## Painel de uso

Acesse **http://127.0.0.1:8765** (o painel inicia com o Windows), abra o atalho **"MyHUB MCP - Painel"** ou peça ao
Claude *"abra o painel do myhub"*. O painel, acessível só no seu computador, mostra:

- o status da sua sessão e os créditos;
- se o Claude Desktop e o Claude Code estão conectados;
- gráficos de uso por dia, ferramenta e modelo;
- o histórico de chamadas e as issues;
- um guia de uso.

O conteúdo das conversas nunca é registrado.

## Importante: uma sessão por conta

O MyHUB.IA aceita **uma sessão ativa por conta**. Se você entrar no site pelo seu navegador normal, o Claude perde
o acesso, e vice-versa. Para usar o site junto com o Claude, abra-o pelo atalho **"MyHUB.IA (sessão do MCP)"**.
Se o Claude disser que a sessão expirou, abra esse atalho e faça login nele.

## Relatório automático de problemas

O MyHUB.IA muda sem aviso. Quando algo quebrar, o Claude abre sozinho uma issue no repositório do projeto,
**sem o conteúdo das suas conversas**, só os dados técnicos do erro. Para o envio ser automático, deixe o
GitHub CLI autenticado com a conta que tem acesso ao repositório:

```powershell
winget install GitHub.cli
gh auth login
```

Sem ele, o Claude abre no navegador a página da issue já preenchida, e você só clica em enviar.

## Problemas?

Rode `myhub doctor`: ele diz o que falta e como resolver. 
O log da instalação fica em `%TEMP%\myhub-mcp-install.log`. Envie-o junto com a mensagem de erro para quem
compartilhou este instalador com você.
