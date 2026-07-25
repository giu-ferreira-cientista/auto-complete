# AutoComplete para Windows

Autocompletar **global** para Windows — sugestões de palavras em praticamente
qualquer campo de texto do sistema, inspirado no **SwiftKey** (aprendizado
contínuo) e no **IntelliSense** (velocidade). Funciona offline, é leve e aprende
com o que você digita.

### ⬇️ [Baixar a última versão](https://github.com/giu-ferreira-cientista/auto-complete/releases/latest)

Baixe o `AutoComplete.exe` na seção **Assets** da release, dê dois cliques e
pronto — não precisa instalar nada.

---

## ✨ Recursos

- **Sugestões em qualquer app** — Chrome, Word, Bloco de Notas, apps Electron e
  outros campos de texto.
- **Dicionário completo pt-BR + inglês** (~87 mil palavras) com ranking por
  frequência de uso.
- **Correção de digitação** — errou "progrmação"? Ele sugere "programação".
- **Sem sensibilidade a acento** — digite "voce", complete "você".
- **Aprendizado contínuo** — aprende as palavras novas que você usa (nomes,
  jargão, siglas) e as prioriza nas sugestões.
- **Popup discreto** junto ao cursor — **TAB** completa, **ESC** fecha,
  **↑/↓** navegam.
- **Ícone na bandeja** — Ativar/Desativar, Iniciar com o Windows, Sair.
- **Aviso de atualização** — quando sai uma versão nova, o app avisa na bandeja.

## 🚀 Como usar

1. Baixe e dê dois cliques em `AutoComplete.exe` → aparece o ícone **"A"** na
   bandeja do Windows.
2. Comece a digitar em qualquer campo de texto.
3. No popup de sugestões:
   - **TAB** — completa a palavra selecionada (corrige acento/erro).
   - **ESC** — fecha o popup.
   - **↑ / ↓** — navegam entre as sugestões.

Clique com o botão direito no ícone da bandeja para **pausar**, ligar o
**início automático com o Windows** ou **sair**.

## 🔒 Privacidade e segurança

- **100% offline.** Nada do que você digita sai da sua máquina.
- **Campos de senha são ignorados** — o app não captura nem aprende nada em
  campos de senha.
- O aprendizado fica **só no seu computador** (em `%LOCALAPPDATA%\AutoComplete`).

> ⚠️ **Aviso do Windows na primeira execução:** como o executável ainda não é
> assinado digitalmente e o app monitora o teclado (para sugerir enquanto você
> digita), o Windows SmartScreen pode mostrar *"O Windows protegeu o
> computador"*. Clique em **"Mais informações" → "Executar assim mesmo"**. O
> antivírus pode alertar pelo mesmo motivo — não é vírus.

## 💻 Requisitos

- **Windows 64-bit** (10 ou 11).
- Nenhuma dependência — o executável é autossuficiente.
- A **primeira execução** leva alguns segundos a mais (descompacta e monta o
  cache do dicionário); as seguintes são rápidas.

## ⚙️ Como funciona (resumo técnico)

- Captura de teclado via hook global de baixo nível (`WH_KEYBOARD_LL`), com
  arquitetura *callback mínimo → fila → worker* para nunca travar o sistema.
- Dicionário em **marisa-trie** (busca por prefixo) + camada mutável para o
  aprendizado do usuário; ranking por frequência, recência e origem.
- Correção de digitação com **RapidFuzz**, só quando o prefixo não casa.
- Descoberta da posição do cursor via **UI Automation** (com fallback Win32).
- Interface em **PySide6**; empacotado com **PyInstaller**.

## 🔄 Atualizações

O app verifica automaticamente se há uma versão mais recente e avisa na bandeja,
com um link para baixar. As versões ficam sempre em
**[Releases](https://github.com/giu-ferreira-cientista/auto-complete/releases)**.

---

*Projeto pessoal em evolução. Feedback e sugestões são bem-vindos via
[Issues](https://github.com/giu-ferreira-cientista/auto-complete/issues).*
