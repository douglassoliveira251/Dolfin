# Dolfin — Controle Financeiro Pessoal

Aplicativo de finanças pessoais em **arquivo único** (`index.html`), sem backend, sem build step e sem dependências externas além de bibliotecas carregadas via CDN quando necessário. Todos os dados ficam no seu próprio computador, em um arquivo `.json` que você escolhe onde salvar.

## Por que arquivo único?

O Dolfin foi desenhado propositalmente como um único `.html` contendo HTML, CSS e JavaScript. Isso significa:

- **Zero instalação.** Basta abrir o arquivo (ou a página publicada) em um navegador moderno.
- **Seus dados são seus.** Nada é enviado para nenhum servidor. O app lê e grava diretamente em um arquivo `.json` local, usando a [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API) do navegador.
- **Portável.** Você pode copiar o `index.html` para qualquer lugar e ele continua funcionando.

## Como usar

### Opção 1 — Direto pelo GitHub Pages
Acesse a versão publicada deste repositório (ative o GitHub Pages nas configurações do repo, apontando para a branch `main` e a raiz `/`). O link terá o formato:

```
https://<seu-usuario>.github.io/<nome-do-repo>/
```

### Opção 2 — Localmente
1. Baixe o `index.html` deste repositório.
2. Abra o arquivo em um navegador baseado em Chromium (Chrome, Edge, Brave). A File System Access API não tem suporte completo no Firefox/Safari no momento.
3. Na primeira execução, escolha **"Criar novo arquivo"** para gerar seu arquivo de dados `.json`, ou **"Abrir arquivo existente"** se você já tem um.

> **Atenção:** o app precisa rodar via `http(s)://` ou como arquivo local aberto diretamente — algumas permissões de arquivo podem se comportar de forma diferente dependendo de como você o abre. A forma mais consistente é sempre pelo link do GitHub Pages.

## Funcionalidades

- **Lançamentos**: entradas, despesas, transferências, com suporte a recorrência (fixa mensal ou parcelada), despesas de cartão de crédito, e **divisão de um lançamento em múltiplas categorias** com valores individuais.
- **Contas e Cartões de Crédito**: controle de saldo, faturas por competência, pagamento de fatura, limite, arquivamento.
- **Categorias**: hierarquia categoria/subcategoria, com ícones e cores personalizáveis, e opção de arquivar ou excluir (com aviso de impacto no histórico).
- **Orçamento**: planejamento mensal por categoria, comparado ao realizado, com saldo previsto considerando também aportes de investimento.
- **Metas**: acompanhamento de objetivos financeiros com histórico de lançamentos vinculados.
- **Investimentos**: ativos, aportes, resgates e atualizações de valor, com extrato mensal e rentabilidade projetada.
- **Tags**: marcação livre de lançamentos, com contagem de uso e remoção rápida no formulário.
- **Dashboard**: KPIs, gráfico de fluxo de caixa com saldo acumulado, comparativo com o mês anterior, variação por categoria, últimas transações.
- **Menu lateral colapsável** e barra de topo unificada (navegação de mês, busca global, notificações, perfil).
- **Modo escuro** e paleta de identidade visual própria (navy/teal).

## Arquitetura

- **Stack**: JavaScript vanilla (sem frameworks), CSS puro, HTML gerado via template strings.
- **Persistência**: File System Access API (`showOpenFilePicker` / `showSaveFilePicker`), com fallback de reconexão via IndexedDB (guarda a referência do handle do arquivo entre sessões).
- **Schema**: todo o estado é normalizado por uma função `normalizeState()`, que faz a migração automática de arquivos `.json` de versões anteriores — abrir um arquivo antigo nunca quebra o app.
- **Sem dependências de build**: não há `npm install`, bundler ou transpilador. O que está no `index.html` é exatamente o que roda no navegador.

## Formato dos dados

Seus dados ficam em um único arquivo `.json`, com esta estrutura principal:

```
{
  "lancamentos": [...],
  "contas": [...],
  "cartoes": [...],
  "categorias": [...],
  "orcamentos": [...],
  "metas": [...],
  "investimentos": { "ativos": [...], "aportes": [...], "atualizacoes": [...] },
  "tags": [...],
  "configuracoes": {...},
  "perfil": {...}
}
```

Esse arquivo nunca é versionado neste repositório — é pessoal e fica só no seu computador.

## Publicando no GitHub Pages

1. Faça push do `index.html` para a branch `main`.
2. Nas configurações do repositório, vá em **Settings → Pages**.
3. Em **Source**, selecione a branch `main` e a pasta `/ (root)`.
4. Aguarde alguns minutos — o GitHub publica automaticamente em `https://<seu-usuario>.github.io/<nome-do-repo>/`.
5. Toda vez que um novo `index.html` for enviado (`git push`), a página publicada atualiza sozinha.

## Versionamento

Este projeto segue um changelog manual em [`CHANGELOG.md`](./CHANGELOG.md), com uma entrada por versão publicada. A partir do ciclo `1.6`, o esquema de versão é `X.Y.NNN`, onde `NNN` é o total acumulado de alterações individuais desde o início daquele ciclo (não incrementa 1 por rodada — soma a quantidade de mudanças feitas). Cada versão relevante deve receber uma tag Git correspondente:

```bash
git tag v1.7.045
git push --tags
```

## Contribuindo (uso pessoal)

Este é um projeto de uso pessoal, desenvolvido de forma iterativa. Não há CI/CD, testes automatizados no repositório ou processo de PR formal — as mudanças são feitas diretamente na branch `main`, uma versão de cada vez.
