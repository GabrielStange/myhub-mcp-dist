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

É só isso. O instalador:

1. prepara o Python (via [uv](https://docs.astral.sh/uv/)), sem mexer em nada que você já tenha instalado;
2. abre um navegador para você **entrar na sua conta do MyHUB.IA**. A senha fica só no navegador; o instalador nunca a vê;
3. conecta o MyHUB ao **Claude Code** e ao **Claude Desktop**. O Claude Desktop é reiniciado automaticamente;
4. cria o atalho **"MyHUB.IA (sessão do MCP)"** na área de trabalho.

No final, você deve ver algo assim:

```
MyHUB MCP 0.2.0 - instalador
  Python (uv) ......................... ok
  Pacote MyHUB MCP 0.2.0 .............. ok

Configurando o MyHUB MCP
  [1/5] Navegador para login .......... ok
  [2/5] Login no MyHUB.IA ............. ok (607 de 1000 créditos)
  [3/5] Claude Code ................... ok
  [4/5] Claude Desktop ................ reiniciando o app... conectado (14 ferramentas)
  [5/5] Atalho do site ................ ok
```

Pré-requisitos: Windows 10/11 e o Claude Desktop e/ou o Claude Code já instalados
([Claude Desktop](https://claude.ai/download) · Claude Code: `irm https://claude.ai/install.ps1 | iex`).

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

## Atualizar, verificar e desinstalar

| Ação | Comando no PowerShell |
|---|---|
| Atualizar | rode o mesmo comando de instalação |
| Verificar (não gasta créditos) | `& "$env:APPDATA\uv\tools\myhub-mcp\Scripts\myhub-doctor.exe"` |
| Desinstalar | `& "$env:APPDATA\uv\tools\myhub-mcp\Scripts\myhub-setup.exe" --uninstall; uv tool uninstall myhub-mcp` |

Seus dados (a sessão do MyHUB) ficam em `%LOCALAPPDATA%\myhub-mcp`. Não compartilhe essa pasta.

## Problemas?

O log da instalação fica em `%TEMP%\myhub-mcp-install.log`. Envie-o junto com a mensagem de erro para quem
compartilhou este instalador com você.
