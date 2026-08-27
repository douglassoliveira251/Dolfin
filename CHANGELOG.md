# Changelog — Dolfin

Todas as mudanças relevantes deste projeto serão documentadas neste arquivo.
Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/).

## [1.5.7] - 2026-08-27

Rodada de correções críticas de cálculo, novo KPI de Fluxo de Caixa no Dashboard, e diversos refinamentos visuais e de usabilidade.

### Added
- **Novo KPI "Fluxo de caixa"** no Dashboard: gráfico de linha com Entradas, Saídas e Saldo acumulado, com seletor de período (7D/30D/3M/6M/12M) e agregação semanal para reduzir ruído visual em períodos longos
- Saudação "Bem-vindo, [nome]" no topo do Dashboard
- **Histórico de consumo no Orçamento** ("Evolução mensal"): mostra a média dos últimos 6 meses com dados (ou menos, se não houver histórico suficiente) e um gráfico de linha da evolução, com botão "Usar este valor" para aplicar a média diretamente como valor orçado
- Campo de **bandeira do cartão** (Mastercard, Visa, Outros) com logo, e campo de **últimos 4 dígitos**, no formulário de cartão
- Configuração "Mostrar apenas contas com saldo" agora também compatível de forma consistente com o Dashboard
- Ícones de editar/excluir diretos (sem menu de contexto) em Cartões e Metas

### Fixed
- **Crítico:** orçamentos definidos no nível de subcategoria apareciam sempre zerados no "Realizado", mesmo com lançamentos reais — causado por uma comparação que só verificava a categoria-pai, nunca a subcategoria
- **Crítico:** saldos de conta podiam aparecer como "-R$ 0,00" (negativo) mesmo sendo efetivamente zero, devido a resíduo de arredondamento de ponto flutuante acumulado em somas sucessivas — corrigido na origem do cálculo, não apenas na exibição
- **Crítico:** ativar parcelamento com divisão por categoria já configurada podia duplicar o valor total do lançamento, ignorando a escolha entre "Valor é Total" ou "Valor é Parcela"
- Cor do saldo consistente com o valor exibido em todos os lugares (Dashboard, tela de Contas, KPIs)

### Changed
- Barras de progresso do Orçamento usam cor fixa por tipo (verde/vermelho/azul), sem variar conforme o percentual de execução
- "Valor planejado" renomeado para "Valor orçado"
- "Aportes (Orçamento)" renomeado para "Aportes" (compatível com arquivos já existentes)
- Botão de excluir do Orçamento movido do rodapé para um ícone no cabeçalho do modal
- Layout do topbar: título/subtítulo de página removidos, controle de mês centralizado, campo de busca mais estreito
- Formulário de cartão reorganizado: Conta vinculada, Bandeira e Últimos 4 dígitos na mesma linha
- Nome sugerido para novo arquivo de dados alterado para `dbase.json`
- Diversos ajustes de espaçamento e tamanho de fonte no Dashboard, Cartões e Orçamento

## [1.5.6] - 2026-08-25

Versão consolidada com o redesenho visual completo (identidade navy/teal, modo escuro), a reformulação das telas de Lançamentos, Categorias, Orçamento e Cartões, e a implementação de multicategoria e parcelamento avançado.

### Added
- **Divisão de lançamentos em múltiplas categorias**, com valores individuais por categoria, dentro de um único registro (sem duplicar lançamentos)
- Suporte à multicategoria combinada com parcelamento, respeitando o modo "Valor é Total" ou "Valor é Parcela"
- Botão "Sair" na barra superior, com confirmação antes de desconectar do arquivo
- Tecla ESC fecha modais e telas abertas
- Metas: lançamento de saldo inicial automático ao definir valor já acumulado na criação; campo de descrição
- Tags: contagem de uso e renomeação por clique
- Card de cada cartão mostra o valor da fatura atual e a data de vencimento

### Fixed
- **Crítico:** lançamentos excluídos podiam reaparecer ao atualizar a página logo em seguida — a exclusão agora é sempre salva no arquivo imediatamente, sem espera
- **Crítico:** editar um lançamento com multicategoria não carregava as categorias originais corretamente
- **Crítico:** ativar parcelamento com divisão por categoria já configurada calculava o valor incorretamente, podendo dobrar o total do lançamento
- **Crítico:** hover de botões e campos usava duas regras de cor conflitantes, causando um verde-claro inconsistente com a identidade visual
- Categoria não carregava automaticamente ao ativar multicategoria em despesas sem histórico prévio

### Changed
- Paleta de cores redesenhada (navy/teal), incluindo modo escuro e tela de inicialização
- Lista de Lançamentos, fatura do cartão e Últimas Transações mostram "Multicategoria" com ícone genérico quando o lançamento tem divisão
- Gráficos e relatórios (Top Categorias, Orçamento, comparativo com mês anterior) contam corretamente cada parte de um lançamento multicategoria na sua respectiva categoria
- Telas de Lançamentos, Categorias, Orçamento e Configurações reorganizadas com abas em formato de cartão e ícones
- Parcelamentos agrupados nas Últimas Transações, mostrando apenas a primeira parcela com o valor total

## [1.0.0] - 2026-07-24 00:00

### Added

**Arquitetura**
- Estrutura single-file HTML/CSS/JS, sem backend, seguindo padrão TYVRA
- Persistência via File System Access API (JSON local, sem localStorage)
- Reconexão automática ao arquivo via handle salvo em IndexedDB
- `normalizeState()` para garantir schema consistente e migrações seguras
- `openConfirmPortal()` substituindo `window.confirm()` nativo
- Autosave (debounce) + commit forçado em `visibilitychange` e `beforeunload`

**Dashboard**
- Ledger strip com Saldo Inicial do mês, Saldo Atual e Saldo Previsto
- Navegação por mês (anterior/próximo)
- KPIs: receitas, despesas, resultado do mês, patrimônio investido, rentabilidade média
- Gráfico de saldo por conta e top categorias de despesa do mês

**Contas**
- CRUD completo (nome, tipo, saldo inicial, cor)
- Cálculo de saldo por conta considerando lançamentos efetivados/previstos

**Cartões**
- CRUD completo (dia de fechamento, dia de vencimento, limite, conta vinculada)
- Visualização de fatura por cartão e por mês, com status Aberta/Fechada

**Categorias e Tags**
- Categorias em 2 níveis (categoria e subcategoria)
- Tipo de categoria vinculado a Entrada ou Despesa
- CRUD de tags para análises transversais às categorias

**Lançamentos**
- CRUD completo com tipos: Entrada, Despesa, Transferência
- Troca de tipo do lançamento (recalcula sinal e limpa vínculos incompatíveis)
- Seleção multi-categoria e multi-tag
- Recorrência (mensal, quinzenal, semanal, anual) com geração automática de 12 ocorrências
- Status Efetivado/Previsto por lançamento
- Filtros por tipo, conta e categoria

**Orçamento**
- Definição de orçamento por categoria (nível 1 ou 2)
- Opção de orçamento fixo (repete todo mês) ou específico de um mês
- Comparativo Planejado x Realizado com barra de progresso e alerta de estouro

**Investimentos**
- Cadastro de ativos por tipo (Renda Fixa, Tesouro Direto, Ações, FII, Fundos, Cripto, Previdência, Outro)
- Registro de aportes e resgates por ativo
- Atualização de valor de mercado por ativo
- Cálculo de rentabilidade por ativo e rentabilidade média da carteira
- KPIs consolidados: total aportado, valor atual da carteira, rentabilidade acumulada

### Known limitations
- Rentabilidade calculada como ganho acumulado simples (valor atual vs. total aportado), sem XIRR/CAGR/anualização
- Edição de lançamento recorrente afeta apenas a ocorrência selecionada; ainda não há opção "editar toda a série"
- Bug visual reportado no ITOps ("..") não se aplica a este projeto — item específico do módulo de Certificados
