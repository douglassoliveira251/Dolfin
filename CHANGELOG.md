# Changelog — Dolfin

Todas as mudanças relevantes deste projeto serão documentadas neste arquivo.
Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/).

## Convenções

### Tipos de alteração

- **Added** — Novas funcionalidades.
- **Changed** — Alterações em funcionalidades existentes.
- **Fixed** — Correções de bugs.
- **Removed** — Funcionalidades removidas.
- **Deprecated** — Funcionalidades que serão removidas futuramente.
- **Security** — Correções relacionadas à segurança.

---

# Release

## [1.5.3] - 2026-08-21

### Fixed
- **Crítico:** ao ativar a divisão por categoria em um lançamento sem nenhuma categoria previamente selecionada (por exemplo, o primeiro lançamento de despesa de um usuário), a primeira linha da divisão ficava sem categoria — corrigido para sempre carregar uma categoria e subcategoria válidas automaticamente

### Changed
- Tela de Cartões: revertido para o layout mais simples, com o valor da fatura atual e a data de vencimento posicionados mais acima, ao lado do nome do cartão
- Na divisão por categoria do lançamento, a soma das categorias foi movida para a mesma linha do botão de adicionar categoria, e o botão foi renomeado para "+ Categoria"
- Quando um lançamento parcelado é configurado por valor de parcela, o valor total agora aparece corretamente alinhado à direita, na mesma linha do rótulo "Valor *"

## [1.5.2] - 2026-08-21

### Added
- No formulário de lançamento, ao configurar um parcelamento por valor de parcela, o valor total do parcelamento agora aparece ao lado do campo "Valor" e se atualiza automaticamente enquanto você digita (não se aplica a lançamentos recorrentes mensais fixos)

### Changed
- Opção de "Dividir em mais de uma categoria" transformada em um botão liga/desliga, no mesmo estilo do "É despesa de cartão?"
- Ao ativar a divisão por categoria, a primeira linha já vem preenchida com a categoria selecionada e o valor total do lançamento; a segunda linha fica em branco para o usuário completar
- Cada linha de divisão por categoria agora também exige a escolha da subcategoria, no mesmo formato usado quando a divisão está desativada
- Passa a ser obrigatório selecionar pelo menos 2 categorias e subcategorias completas para salvar um lançamento dividido
- Card de cada cartão na tela de Cartões com espaçamento reduzido, ocupando menos altura

## [1.5.1] - 2026-08-21

### Added
- Nova opção "Dividir este lançamento em mais de uma categoria" no formulário de lançamento (entradas e despesas). Ao ativar, é possível indicar duas ou mais categorias com valores individuais, desde que a soma seja igual ao valor total — o sistema gera um lançamento para cada categoria, vinculados entre si

### Changed
- No formulário de lançamento, a Data de efetivação passou a aparecer antes da Data de lançamento, ambas dentro de "Mais opções", sem os rótulos separados de "Hora"
- No card de cada cartão na tela de Cartões, o alerta de pendência foi movido para o canto superior direito, e o valor da fatura atual com sua data de vencimento passaram para o canto inferior direito

### Fixed
- **Crítico:** ao salvar um lançamento dividido em múltiplas categorias, os valores individuais não estavam sendo lidos corretamente do formulário, fazendo o valor total ser atribuído à primeira categoria e zero às demais — corrigido

## [1.5.0] - 2026-08-21

### Added
- Botão "Sair" e os demais ícones da barra superior padronizados visualmente, mantendo o propósito de cada um
- Tecla ESC agora fecha a tela/modal aberta no momento
- Card de cada cartão na tela de Cartões passou a mostrar o valor da fatura atual e a data de vencimento no canto direito
- Card "Últimas transações" do Dashboard: lançamentos parcelados agora aparecem como uma única linha (a partir da primeira parcela), com o valor total do parcelamento — lançamentos recorrentes mensais continuam sendo exibidos individualmente

### Fixed
- **Crítico:** o efeito de destaque ao passar o mouse sobre botões e campos de formulário usava duas regras de cor conflitantes, causando um tom verde-claro chocante com a paleta atual — corrigido na origem, junto com os mesmos pontos em seletores de mês, campos e chips
- **Crítico:** o novo indicador de fatura atual na tela de Cartões quebrava a tela inteira devido a uma função interna que retorna texto onde um objeto de data era esperado — corrigido

### Changed
- Data de efetivação movida para dentro de "Mais opções" no formulário de lançamento, agora na mesma linha da Data de Lançamento

## [1.4.24] - 2026-08-21

### Added
- Botão "Sair" adicionado na barra superior, ao lado do botão de ocultar valores, com confirmação antes de desconectar do arquivo

### Changed
- A ação de desconectar do arquivo foi removida do clique em "Última sincronização" e passou a ficar exclusivamente no novo botão "Sair"
- No card de Cartões do Dashboard, o destaque foi removido dos textos fixos "Vence em" e "Próxima fatura:", mantendo a ênfase apenas na data e no valor
- Fonte dos valores na lista de Lançamentos ajustada para um meio-termo entre o texto normal e o negrito total, reduzindo um pouco o destaque anterior

## [1.4.23] - 2026-08-21

### Added
- Tags agora mostram a quantidade de lançamentos/aportes associados ao lado do nome
- Clicar em uma tag abre um modal para renomeá-la (antes só era possível criar ou excluir)

### Fixed
- **Crítico:** ao passar o mouse sobre uma categoria, o destaque aparecia em dourado — duas regras de hover conflitantes faziam a cor amarela sempre vencer sobre o cinza pretendido. Corrigido na origem

### Changed
- Tela de inicialização: botão "Criar novo arquivo" e o slogan atualizados da paleta dourada antiga para a nova identidade verde-escuro/teal
- Títulos de páginas e cards no modo escuro trocados de verde-teal para branco
- No card de Cartões do Dashboard, a data de vencimento e o valor da próxima fatura ganharam um leve destaque adicional
- Fonte dos valores na lista de Lançamentos ajustada para ser idêntica à do campo Nome (mesmo tamanho e tipo), diferenciando-se apenas pelo negrito
- Abas de Lançamentos, Categorias, Orçamento e Configurações: reduzido o destaque de peso da fonte na aba selecionada, mantendo apenas uma linha inferior mais fina como indicador

## [1.4.22] - 2026-08-21

### Changed
- Paleta de cores do modo escuro modernizada, trocando os tons esverdeados antigos por uma base navy/teal coerente com a identidade visual atual do Dolfin
- Gradiente de fundo da tela de inicialização atualizado para os novos tons da marca
- Tela de Lançamentos: KPIs de resumo removidos; uma linha de total foi adicionada ao final da tabela, refletindo o saldo de todos os itens filtrados
- Números da tela de Lançamentos padronizados com a mesma fonte dos KPIs do Dashboard, em negrito, em todas as abas (Todos, Entradas, Despesas, Transferências, Investimentos)
- Abas de Lançamentos, Categorias, Orçamento e Configurações: a aba selecionada agora ganha uma linha colorida na parte inferior para maior destaque
- Botões de criação em Categorias e Orçamento movidos para o canto direito da linha de abas, renomeados para "+ Categoria" e "+ Orçamento"

## [1.4.21] - 2026-08-21

### Changed
- Fundo da barra de busca e dos menus de resultados/alertas corrigido para respeitar o modo escuro, em vez de ficar branco fixo
- Abas de tipo (Entrada/Despesa/Transferência) no formulário de lançamento não ficam mais fixas ao rolar a tela — sobem junto com o conteúdo
- Abas de Lançamentos, Categorias, Orçamento e Configurações redesenhadas: fundo branco/destacado, ícone ao lado de cada nome (na mesma cor da fonte), e cores mais fortes quando selecionadas
- Lista de Lançamentos: nova aba "Todos" adicionada e definida como padrão ao abrir a tela; linha divisória entre lançamentos deixada mais sutil, com o conteúdo mais compacto; valores com destaque visual maior (negrito)
- Lista de Categorias reorganizada no mesmo padrão visual usado em Orçamentos — um único container de lista, em vez de cards separados para cada categoria

## [1.4.20] - 2026-08-21

### Fixed
- **Crítico:** o card "Últimas transações" ordenava pela data de vencimento ("Data e hora" do formulário) em vez da "Data do lançamento" (campo disponível em "Mais opções"). Corrigido para ordenar corretamente pela Data do lançamento, e a data exibida em cada linha do card agora reflete esse mesmo campo

## [1.4.19] - 2026-08-21

### Fixed
- **Crítico:** o card "Últimas transações" do Dashboard não mostrava lançamentos recentes reais quando havia compras parceladas antigas na base — a ordenação usava o momento de criação do registro no sistema, que para parcelamentos reflete quando a compra original foi feita, não a data relevante de cada parcela. Corrigido para ordenar diretamente pela data do lançamento, do mais recente para o mais antigo, incluindo lançamentos futuros (parcelas a vencer), permitindo ajuste manual quando necessário

### Verified
- Confirmado que a data do lançamento já era exibida abaixo do valor em cada linha do card "Últimas transações"

## [1.4.18] - 2026-08-21

### Fixed
- **Crítico:** a ordenação do card "Últimas transações" ainda podia mostrar lançamentos por data de vencimento em vez de data de criação, especialmente em parcelamentos — parcelas futuras (ex: 3/3, vencendo meses à frente) apareciam como se fossem a transação mais recente. Corrigido o critério de desempate na ordenação para respeitar corretamente a ordem cronológica das parcelas

### Changed
- Cor de seleção de texto trocada de amarelo/dourado para verde-água, alinhada à nova paleta
- Contorno de campos de formulário ao clicar (foco) trocado de amarelo para cinza escuro
- Links de ação ("+X mais" no sino de alertas, "Criar tag") trocados de dourado para o verde escuro da identidade
- Barras de progresso dos orçamentos (na tela de Orçamento e no card do Dashboard) agora seguem 3 faixas de cor: verde escuro até 70%, amarelo de 70% a 95%, vermelho a partir de 95%

## [1.4.17] - 2026-08-21

### Changed
- Cor de seleção de texto e das tags trocada de dourado/amarelo para tons de verde-água, alinhados com a nova paleta do sistema
- Ordenação do card "Últimas transações" ajustada para usar a data de lançamento (o campo "Data e hora" do formulário), do mais recente para o mais antigo
- Gráfico "Top categorias de despesa" aumentado, com o valor central em fonte menor e negrito

## [1.4.16] - 2026-08-21

### Added
- Campo "Data e hora do lançamento" nas opções avançadas do formulário de lançamento — inicia oculto, pré-preenchido com o momento atual, revelado ao clicar em "Mais opções". Usado para ordenar as transações recentes, sem afetar a data de vencimento ou de efetivação

### Changed
- Ordenação do card "Últimas transações" corrigida para refletir quando o lançamento foi de fato criado no sistema, não a data de vencimento
- Fonte do valor central no gráfico "Top categorias de despesa" padronizada com o mesmo tamanho e peso do "Saldo inicial"
- Linhas dos cards de Contas e Cartões no Dashboard compactadas, com fonte de valor levemente reduzida

### Fixed
- **Crítico:** o campo de data/hora do lançamento não era salvo ao clicar em "Salvar" — a função de gravação lia os campos do formulário diretamente e não incluía esse novo campo

## [1.4.15] - 2026-08-21

### Fixed
- **Crítico:** o botão "Ver todas" no card de Contas do Dashboard estava direcionando para a tela de Cartões em vez de Contas

### Added
- Botão "Ver todas" no card de Cartões do Dashboard, direcionando para a tela de Cartões

### Changed
- Card "Últimas transações" movido para abaixo de "Orçamento do mês" e "Metas em aberto"
- Ordenação das transações no card corrigida para usar a data do lançamento, não a data de efetivação
- Aba "Saídas" renomeada para "Despesas" no card de Últimas transações
- Linhas do card de Últimas transações compactadas
- Linha divisória cinza removida das listas de Contas, Cartões e Últimas transações no Dashboard
- Fonte de todos os valores monetários nos KPIs do Dashboard padronizada com o mesmo tamanho e peso usados no "Saldo inicial"

## [1.4.14] - 2026-08-21

### Added
- Novo card "Últimas transações" no Dashboard, com abas para filtrar entre Todas, Entradas e Saídas, mostrando os 5 lançamentos mais recentes com categoria, valor e data. Inclui atalhos para a tela de Lançamentos e clique direto em cada item para edição

## [1.4.13] - 2026-08-21

### Changed
- Card "Contas" do Dashboard redesenhado com layout mais compacto, seguindo o modelo de referência: cabeçalho com botão "Ver todas" (que leva à tela de Cartões), linhas mais enxutas e seta indicativa no lugar do botão de detalhe separado

## [1.4.12] - 2026-08-21

### Fixed
- **Crítico:** o sino de alertas só verificava faturas de cartão vencidas dentro dos últimos 3 meses — faturas fechadas e não pagas há mais tempo deixavam de ser sinalizadas silenciosamente. Corrigido para verificar qualquer competência de fatura com pendência, sem limite de tempo

### Changed
- Cor de fundo do favicon do sistema alterada para a mesma cor do botão "+" flutuante
- No card de cada cartão na tela de Cartões, o sinalizador de status/pendência da fatura foi movido para a direita, na mesma linha do nome do cartão, em vez de ficar em uma linha separada abaixo

## [1.4.11] - 2026-08-21

### Added
- Linha de total por banco na tela de Investimentos agora mostra a média de rentabilidade (1 mês, 3 meses, último ano e projeção anual) dos ativos daquele banco, em vez de ficar em branco

### Changed
- Todos os botões escuros de ação (Salvar, Adicionar, e variações) padronizados na mesma cor do botão "+" flutuante
- Tamanho e espaçamento entre letras do "DOLFIN" ajustados para que a largura do texto fique igual à de "Finanças Pessoais" logo abaixo
- Espaçamento entre o rótulo "Saldo atual" e o valor reduzido no Dashboard
- Cor dos textos do menu lateral, e-mail de perfil e informações de sincronização trocada de um tom amarelado/bege para um cinza neutro — mantendo cores de destaque apenas em elementos de identidade (avatar) e status (indicador de conexão)
- Título e subtítulo duplicados removidos de todas as telas internas (Lançamentos, Contas, Cartões, Categorias, Tags, Orçamento, Metas, Investimentos, Configurações) — agora aparecem apenas na barra superior, com a mesma formatação de fonte que tinham antes

## [1.4.10] - 2026-08-21

### Changed
- Logo do Dolfin substituído pela imagem oficial fornecida (processada com fundo transparente), tanto no menu lateral quanto na tela de conexão inicial — removido o badge quadrado de fundo, ícone agora aparece sozinho na cor teal original
- Favicon atualizado com o novo desenho do golfinho sobre fundo verde arredondado
- Cor de fundo do sistema ajustada de um tom creme amarelado para um cinza neutro sutil
- Fonte do texto "DOLFIN" no menu lateral ajustada para uma tipografia mais arredondada, aproximando da identidade visual de referência
- Subtítulo "Finanças Pessoais" no menu lateral corrigido: texto normal (não mais todo em maiúsculo), cor branca, e mesma fonte usada nos itens de menu

## [1.4.9] - 2026-08-21

### Changed
- Fonte do sistema definida como Segoe UI (com fallbacks para Mac/Linux), removendo a referência à Inter que não carregava de fato
- Títulos dos KPIs da primeira e segunda linha do Dashboard não ficam mais em caixa alta — agora seguem o mesmo padrão visual (cor, peso e tamanho) dos títulos usados na tela de Contas
- Valores dos KPIs padronizados no mesmo tamanho e peso usados na tela de Contas
- Espaçamento do card "Saldo atual" ajustado, corrigindo a sobreposição entre o percentual de variação e o mini-gráfico
- Ícone do sino de alertas redesenhado: fundo neutro sempre, com uma bolinha verde mostrando a quantidade de alertas (em vez de mudar a cor do botão inteiro para vermelho)
- Botão de ocultar valores ganhou a mesma base visual do sino, sem indicador de alerta
- Logo do Dolfin atualizado: texto "DOLFIN" com peso mais forte e o ícone redesenhado como um golfinho saltando com barras de crescimento, mais próximo da identidade visual de referência
- Favicon atualizado com o novo desenho do logo, fundo verde-teal e golfinho branco

## [1.4.8] - 2026-08-21

### Removed
- Card "Destino do resultado" removido do Dashboard

### Changed
- Menu "Resumo financeiro" renomeado para apenas "Resumo" (no menu lateral e no título da tela)
- Cor dos títulos de cards, telas e modais revertida para o verde escuro original — o novo teal do sistema fica restrito a botões e elementos de destaque, não mais aplicado em textos
- Todos os KPIs do Dashboard (primeira e segunda linha) padronizados com o mesmo tamanho de fonte para título e valor, seguindo o padrão de "Receitas efetivadas"
- Card "Saldo atual": ícone restaurado na posição original, mini-gráfico reduzido para um tamanho mais discreto, mantendo a altura padrão de 102px
- Campo de busca global mais largo, com borda um pouco mais escura para melhor visibilidade
- Botões de criar/adicionar (o "+" flutuante, "Novo aporte", "Nova categoria", "Nova conta" e afins) agora usam a mesma cor do item de menu selecionado na barra lateral

## [1.4.7] - 2026-08-21

### Added
- Nova faixa "Destino do resultado" no Dashboard, mostrando quanto do resultado do mês foi investido e quanto ficou disponível em caixa

### Changed
- Cores do sistema padronizadas para a paleta exata definida: sidebar `#0D182D`, menu selecionado `#0B4642`, teal principal do logo `#00B794` — aplicado em toda a aplicação, incluindo o botão "+" flutuante, que agora usa a mesma cor do item de menu selecionado
- Fontes padronizadas: logo (700/20px), título de página (700/24px), subtítulo (400/13px), menu lateral (500/14px), labels (600/11px), valores financeiros (700/22px) — com Inter como fonte preferencial (usa a fonte de sistema como alternativa quando Inter não está instalada, já que o Dolfin funciona 100% offline)
- Todos os KPIs da primeira e segunda linha do Dashboard padronizados para 102px de altura, com o mesmo tamanho de fonte entre as duas linhas
- Mini-gráfico do card "Saldo Atual" aumentado
- **Lógica do "Resultado do mês" corrigida**: agora representa Receitas efetivadas − Despesas efetivadas, sem descontar o valor investido no mês — refletindo o desempenho financeiro real do período, com o percentual da receita como referência ("▲X% da receita")

### Fixed
- **Crítico:** o campo de busca global exibia o texto `${ICONS.search}` literalmente no lugar do ícone de lupa — causado por um trecho de HTML estático que ficou fora do escopo de interpolação do JavaScript. Corrigido preenchendo o ícone dinamicamente ao carregar o sistema

## [1.4.6] - 2026-08-21

### Changed
- Título, subtítulo e busca global do Dashboard movidos para a barra superior (topbar), seguindo o modelo de referência — a busca agora fica disponível em qualquer tela, não só no Resumo
- Ícone de olho removido do card "Saldo Atual" (já existe o botão de ocultar valores no topo)
- Cores do sistema padronizadas para a nova identidade da sidebar: cor primária alterada de verde escuro para azul-marinho em toda a aplicação
- Item de menu selecionado voltou a usar verde claro como destaque, no lugar do azul/teal aplicado anteriormente
- Botão "Desconectar" removido da barra lateral; substituído por um indicador de "Última sincronização" com data e hora, clicável para desconectar (com confirmação)
- Altura dos cards de KPI da primeira linha do Dashboard reduzida, aproximando do layout de

## [1.4.5] - 2026-08-19

### Changed
- Mini-gráfico do card "Saldo Atual" movido para o lado direito da variação percentual, na mesma linha — antes ficava abaixo, ocupando a largura toda do card
- Menu lateral redesenhado: fundo navy escuro, logo em badge quadrado teal com "DOLFIN" e "Finanças Pessoais" alinhados à esquerda, item ativo destacado em teal sólido
- Ordem dos itens do menu reorganizada: Resumo, Lançamentos, Contas, Cartões, Categorias, Metas, Investimentos, Orçamento, Tags
- "Dashboard" renomeado para "Resumo" em todo o sistema (menu, título da tela, cabeçalho superior)

## [1.4.4] - 2026-08-19

### Changed
- Todos os KPIs do Dashboard redesenhados em um único padrão visual: texto (rótulo, valor, nota) alinhado à esquerda, com ícone colorido de fundo suave à direita
- Novo card "Resultado do mês" incluído na primeira linha, ao lado de Saldo Inicial, Saldo Atual e Saldo Previsto
- Cards reorganizados em duas linhas: Saldo Inicial / Saldo Atual / Saldo Previsto / Resultado do mês na primeira; Receitas / Despesas / Investido no mês / Patrimônio investido / Rentabilidade no mês na segunda

### Fixed
- **Crítico:** ícones de Saldo Inicial, Saldo Atual e Saldo Previsto apareciam como "undefined" — causado por um engano ao referenciar ícones de um objeto interno errado do sistema, que não continha essas figuras. Corrigido usando o objeto correto de ícones, com cada um testado individualmente antes da publicação

## [1.4.3] - 2026-08-19

### Changed
- Saldo Inicial, Saldo Atual e Saldo Previsto unificados em um único bloco no Dashboard, com um ícone pequeno (fundo suave) no cabeçalho — mantendo o mesmo layout de conteúdo interno em 3 colunas
- Saldo Inicial e Saldo Previsto agora usam exatamente a mesma formatação de fonte dos demais cards do Dashboard (como "Receitas efetivadas")

### Fixed
- A formatação de fonte de "Saldo Inicial" e "Saldo Previsto" não estava aplicando corretamente por depender de uma classe de estilo vinculada a um contexto específico que não existia mais no novo layout — corrigido com uma regra de estilo genérica, sem impacto em nenhuma outra tela do sistema

## [1.4.2] - 2026-08-19

### Changed
- Card de saldo do Dashboard reorganizado em três quadrantes visuais na mesma linha (Saldo Inicial, Saldo Atual, Saldo Previsto), cada um centralizado dentro do seu próprio espaço
- Mini-gráfico do Saldo Atual reposicionado ao lado do valor e do indicador de variação, com o conteúdo alinhado à esquerda e contido dentro do quadrante — antes ficava abaixo, ocupando a largura toda
- Detalhamento do Saldo Previsto simplificado: "Entradas do mês" e "Despesas do mês" agora somam tudo em uma linha só (efetivado + previsto), em vez de linhas separadas
- Nova linha "Aportes que já saíram das contas" no detalhamento, mostrando apenas os aportes já efetivados com conta vinculada — refletindo o que de fato já saiu do saldo, separado dos aportes ainda previstos

## [1.4.1] - 2026-08-19

### Added
- Detalhamento do Saldo Previsto agora mostra também as entradas e despesas já efetivadas no mês, como ponto de partida do cálculo, antes de somar o que ainda está previsto
- Aviso no comparativo de categorias quando há mais categorias com movimento do que o exibido ("+X categoria(s) com menor variação não exibida(s)")

### Changed
- Card de saldo do Dashboard reorganizado em um único bloco: Saldo Inicial à esquerda, Saldo Atual centralizado (com variação e mini-gráfico), Saldo Previsto à direita — removida a faixa separada que existia abaixo
- Limite de categorias exibidas no comparativo com o mês anterior aumentado de 6 para 8

### Fixed
- **Crítico:** o campo "Efetivado?" não aparecia ao criar um lançamento do tipo Transferência — o campo inteiro estava dentro de um bloco que só era exibido para Entrada/Despesa. Corrigido para aparecer em todos os tipos, com o mesmo comportamento de Entrada e Despesa
- **Crítico:** o comparativo de categorias com o mês anterior podia esconder categorias inteiras quando o gráfico "Top categorias" acima estava com uma categoria selecionada em modo de detalhamento (drill-down) — os dois cálculos estavam compartilhando dados por engano. Agora são independentes

## [1.4.0] - 2026-08-19

### Added
- Card de "Saldo Atual" redesenhado no Dashboard: valor em destaque, variação percentual com seta (▲/▼) comparando com o mês anterior, e um mini-gráfico de evolução dos últimos 7 meses com gradiente suave — inspirado no padrão visual de apps financeiros modernos

## [1.3.23] - 2026-08-19

### Fixed
- **Crítico:** correção anterior da fatura de cartão introduziu uma nova inconsistência — a fatura passou a ser considerada "ainda aberta" no próprio dia do fechamento, contrariando o esperado. Unificado o critério em todas as telas (Dashboard, novo lançamento, detalhe da fatura) para que a fatura feche a partir do dia do fechamento (inclusive), testado no cenário exato do fechamento caindo hoje
- **Crítico:** ao selecionar o ativo de destino no modal de transferência entre ativos, o nome/ícone escolhido não aparecia no campo — causado por um bug na função compartilhada de seletores com ícone, que atualizava o valor internamente mas nunca atualizava visualmente o botão. Corrigido na raiz, beneficiando todos os seletores desse tipo no sistema

### Changed
- Parcelas de despesas de cartão agora mantêm a mesma data e hora da compra original em todas as parcelas futuras — apenas a fatura (competência) avança mês a mês. Parcelamentos sem cartão continuam com a data avançando normalmente, já que não têm uma fatura para controlar o mês separadamente

## [1.3.22] - 2026-08-19

### Fixed
- **Crítico:** o Dashboard, o modal de novo lançamento e a tela de detalhe da fatura usavam três regras de fronteira de data ligeiramente diferentes para decidir se uma fatura estava aberta ou fechada. Isso fazia com que, ao redor do dia de fechamento, o Dashboard já mostrasse a fatura como "Fechada" enquanto o modal de lançamento ainda oferecesse o mês já encerrado como padrão ao ativar "despesa de cartão". As três lógicas foram unificadas para usar o mesmo critério, e testado com o cenário real reportado (fechamento dia 16, hoje dia 19): agora o modal já vem com o mês seguinte selecionado automaticamente, consistente com o que o Dashboard mostra

## [1.3.21] - 2026-08-19

### Changed
- Valor atual e total da meta destacados (fonte maior, negrito) no card "Metas em aberto" do Dashboard
- Opções de ativo no modal de transferência entre ativos agora mostram o nome do banco antes do nome do ativo (ex: "Nubank - CDI 130%"), facilitando identificar a conta de origem/destino

### Investigated
- Comportamento de seleção automática da fatura ao marcar despesa de cartão com a fatura do mês já fechada, e preservação da hora nas parcelas futuras de um parcelamento — testados extensivamente com o cenário exato reportado e confirmados funcionando corretamente. Aguardando mais detalhes caso o problema persista em algum cenário específico

## [1.3.20] - 2026-08-19

### Changed
- Seletor de tipo (Entrada/Despesa/Transferência) no modal de novo lançamento redesenhado no formato de pills arredondados: fundo claro quando não selecionado, preenchimento sólido colorido com texto branco quando selecionado — verde para Entrada, vermelho para Despesa, amarelo/dourado para Transferência

## [1.3.19] - 2026-08-19

### Added
- Botão "Transferir" no extrato do ativo, ao lado de Aporte/Resgate/Atualizar valor

### Changed
- Ao clicar em efetivar um lançamento, a alteração afeta só aquela ocorrência — não pergunta mais se deve aplicar a toda a série recorrente
- Clicar em efetivado sempre registra a data e hora atual do sistema (exceto para despesas de cartão, cujo controle continua vinculado ao pagamento da fatura)
- Card "Metas em aberto" no Dashboard: mostra o valor atual e o total da meta no lugar da porcentagem; a porcentagem passou para o final da barra de progresso
- Transferência entre ativos removida do menu de opções da linha inicial da lista de Investimentos — agora fica dentro da tela de extrato do ativo
- Modal de transferência entre ativos: campos renomeados de "De"/"Para" para "Origem"/"Destino", com seletor visual (ícone + cor do banco vinculado) para facilitar identificar cada ativo
- Transferências entre ativos aparecem com rótulo e cor próprios ("Transferência") no extrato, e não são mais contabilizadas como aporte — não afetam o total aportado nem o rendimento do ativo, só o valor atual

### Fixed
- Clique em efetivado em lançamentos fixos ou parcelados fora de cartão não usava consistentemente a data/hora atual do sistema

## [1.3.18] - 2026-08-13

### Changed
- Cálculo da projeção anual de rendimento em Investimentos alterado: agora usa a média do rendimento mensal dos últimos 3 meses, aplicada compostamente pelos 12 meses do ano, em vez da rentabilidade acumulada desde o início do ativo
- Cabeçalho da coluna "Último ano" passou a incluir "/Projetado" com destaque reduzido
- Texto "projeção:" removido da célula, mostrando apenas os dois percentuais lado a lado

## [1.3.17] - 2026-08-13

### Changed
- Fonte do valor central no gráfico de Top Categorias do Dashboard reduzida
- Legenda do gráfico de Top Categorias: texto deslocado um pouco mais para a direita, mostrando o valor em R$ no lugar do percentual
- Coluna "Total / ano" da tela de Investimentos renomeada para "Último ano" — o valor principal agora reflete o rendimento efetivo dos últimos 12 meses daquele ativo, com a projeção anualizada (baseada em todo o histórico coletado) exibida ao lado

## [1.3.16] - 2026-08-13

### Added
- Drill-down no gráfico de "Top categorias de despesa" do Dashboard: clicar no nome de uma categoria com subcategorias atualiza o gráfico para mostrar a composição interna, com botão "Voltar" para retornar à visão anterior
- Ícone de detalhamento dedicado ao selecionar uma fatia do gráfico, abrindo o extrato daquela categoria

### Changed
- Valor total (ou da fatia selecionada) agora aparece dentro do círculo vazio do gráfico de Top Categorias, com o percentual quando algo está selecionado
- Legendas do gráfico de Top Categorias simplificadas: só nome e percentual, sem repetir o valor em R$
- Botão de modo escuro/claro no menu lateral trocou o formato on/off por um único botão que muda de ícone (lua/sol) e texto ("Modo escuro" ↔ "Modo claro") conforme o tema ativo
- Tela de Contas limitada a 4 contas por linha — a partir da 5ª, elas continuam na linha de baixo

### Fixed
- Selo de status "Fechada" no card de cartões do Dashboard aparecia cortado quando o nome do cartão era mais longo — corrigido o layout para acomodar os dois elementos sem truncar

## [1.3.15] - 2026-08-13

### Changed
- Ícone do sino de alertas com fundo vermelho escuro quando há algum alerta ativo, em vez de só mudar a cor do desenho
- Cada item na lista de alertas ganhou uma barra colorida na lateral esquerda identificando o tipo (verde para entrada, vermelho para despesa, dourado para transferência, roxo para fatura), com o valor em destaque ao lado
- Lista de alertas do sino mais larga (320px → 400px)
- Ícones de olho e sino deslocados um pouco para a esquerda, com mais respiro em relação à borda direita da tela

## [1.3.14] - 2026-08-13

### Added
- Dropdown do sino de alertas agora detalha cada item individualmente (nome, categoria, valor, situação), não só a contagem agregada por tipo — com atalho "+ X mais" quando há muitos itens em uma seção
- Clicar em um item específico do alerta abre o lançamento direto para edição

### Changed
- Ícone do sino fica destacado em dourado (não só a bolinha) quando há algum alerta ativo
- Removido o deck de cards de pendências que ficava solto na tela principal do Dashboard — essa informação agora vive só no sino de alertas, evitando repetição

## [1.3.13] - 2026-08-13

### Added
- Ícone de sino de alertas no topo, ao lado do ícone de olho, com indicador visual (ponto vermelho) quando há despesas, entradas, transferências ou faturas pendentes vencendo em até 3 dias ou já vencidas. Clicar abre um resumo por categoria, e cada item leva direto para a lista detalhada correspondente

### Changed
- Ícone de editar foto reduzido na tela de Perfil

## [1.3.12] - 2026-08-13

### Added
- Botão de limpar (x) no campo de busca global, aparecendo apenas quando há texto digitado

### Changed
- Espaçamento maior entre o slogan e o card de perfil no menu lateral
- Círculo da foto reduzido na tela de Perfil
- Botão "Salvar perfil" alinhado à direita

## [1.3.11] - 2026-08-13

### Fixed
- Modal de ajustar foto de perfil com fundo muito escuro, dificultando a leitura do texto — causado por um efeito de sombra que acabava cobrindo o modal inteiro; removido
- Campo de e-mail no Perfil fora do padrão visual do sistema — o tipo do campo (`email`) não estava incluído na lista de estilos padrão; corrigido para usar o mesmo padrão dos demais campos

### Changed
- Campos "Nome" e "E-mail" no Perfil agora ficam na mesma linha
- Card de perfil na sidebar expandido horizontalmente, ocupando a mesma largura dos itens de navegação (menos espaçamento das bordas)
- Fonte do nome dos lançamentos reduzida nos resultados da busca global
- Campo de busca global com fundo branco explícito e borda cinza escura ao ser selecionado

## [1.3.10] - 2026-08-13

### Added
- Tela de Configurações reorganizada em abas: Perfil, Personalização, Arquivo Base e Sobre
- Aba "Perfil" para cadastrar nome, e-mail e foto — com ferramenta de recorte circular (arrastar para posicionar, controle de zoom) ao selecionar uma imagem
- Card de perfil no menu lateral, abaixo do slogan, mostrando foto/iniciais, nome e e-mail — clicável, leva direto para a aba Perfil

### Changed
- Ícone de olho (ocultar/mostrar valores) no topo aumentado para ficar mais visível
- Busca global transformada em um menu suspenso (dropdown) com fundo branco, em vez de aparecer embutida na página — fecha automaticamente ao clicar fora, e cada resultado ganha uma borda cinza suave ao passar o mouse

## [1.3.9] - 2026-08-11

### Added
- Busca global no Dashboard: encontra lançamentos, categorias, contas, cartões, tags, ativos de investimento e metas ao mesmo tempo, com resultados clicáveis que abrem direto na tela correspondente
- Ícone de olho no topo (ao lado do controle de mês), para ocultar/mostrar todos os valores financeiros do sistema
- Opção "Ocultar valores ao abrir" em Configurações > Personalização, desativada por padrão

### Changed
- Campo de valor no detalhamento de Metas mais largo horizontalmente
- Card de cartões no Dashboard agora sempre mostra a data de vencimento da fatura atual e o valor da próxima fatura, independente do status (aberta, fechada ou paga)
- Categoria interna "Aportes (orçamento)" (usada só para o orçamento de investimento) agora fica oculta na tela de Categorias

## [1.3.8] - 2026-08-11

### Changed
- No detalhamento da Meta, "Adicionar valor" e "Data" foram movidos para baixo de "Meta alcançada" (que agora fica em linha própria), com o botão "Adicionar" ao lado dos dois campos, tudo na mesma linha

### Fixed
- **Crítico:** o Saldo Previsto de meses futuros não considerava despesas/entradas que já estavam pendentes em meses anteriores e ainda não tinham sido pagas — elas simplesmente desapareciam da projeção, fazendo o saldo futuro aparecer bem maior do que deveria. Corrigido para acumular todo o pendente até o mês projetado (inclusive), não só o que é específico daquele mês. Testado com os valores reais reportados: a projeção de setembro, que antes ignorava uma despesa pendente de R$4.770,27 de agosto, agora mostra corretamente -R$1.324,28, batendo com a conta manual

## [1.3.7] - 2026-08-09

### Added
- Botão de limpar (x) no campo de busca de Lançamentos, aparecendo apenas quando há texto digitado
- Data de vencimento da fatura atual exibida abaixo do valor no card de cartões do Dashboard

### Changed
- No card de cartões do Dashboard, quando a fatura está fechada aguardando pagamento, o badge mudou de "Pagar até [data]" para apenas "Fechada" — a data de vencimento passou a ficar na linha do valor
- Layout do detalhamento de Meta otimizado: campo de data e botão "Adicionar" agora na mesma linha

## [1.3.6] - 2026-08-09

### Changed
- No detalhamento da Meta, o texto "Meta alcançada" ficou mais próximo do switch de ativação
- Campo de valor em "Adicionar valor" aumentado (mais largo e mais alto), com fonte maior para facilitar a digitação

## [1.3.5] - 2026-08-09

### Changed
- No detalhamento da Meta, o toggle "Meta alcançada" e o campo "Adicionar valor" agora ficam lado a lado na mesma linha
- Em Lançamentos, o percentual do valor pendente de efetivação passou a ficar ao lado do valor (não mais em linha própria)

## [1.3.4] - 2026-08-09

### Changed
- Total de despesas/entradas em Lançamentos mais destacado visualmente (maior, mais forte) em relação ao bloco de pendente de efetivação ao lado
- Botões "Editar" e "Excluir" da tela de detalhamento de Meta movidos para ícones compactos no cabeçalho, à direita, antes do botão de fechar

## [1.3.3] - 2026-08-09

### Changed
- Resumo de total e pendente de efetivação em Lançamentos movido do cabeçalho para a linha das abas (lado direito), com texto mais discreto e organizado em 3 linhas (total, percentual pendente, valor pendente)
- Telas de "Detalhamento da meta" e "Atualizar progresso" unificadas em uma só: ao abrir uma meta, o campo de adicionar valor (com toggle Entrada/Saída, agora com texto) e o histórico completo já aparecem direto, sem precisar de uma tela extra
- Botões "Editar meta" e "Excluir meta" agora lado a lado na mesma linha; toggle "Meta alcançada" posicionado acima deles
- Card "Comparativo com o mês anterior" no Dashboard: subtítulo removido, o período (ex: "Agosto de 2026 vs Julho de 2026") passou para o lado do título em tom discreto, e os totais foram movidos para o rodapé do card

## [1.3.2] - 2026-08-09

### Changed
- Ordenação de Lançamentos e extratos revertida para usar a data do lançamento (não mais a data de vencimento da fatura para despesas de cartão), com desempate por horário quando duas coisas caem no mesmo dia
- Extrato de fatura agora ordenado do lançamento mais novo para o mais antigo (data e hora)
- Toggle Entrada/Saída no modal de progresso da Meta redesenhado como controle segmentado compacto, com ícones de seta em vez de texto
- Botões de ação da Meta (editar, adicionar valor, excluir) removidos do card na listagem e movidos para uma nova tela de detalhamento, aberta ao clicar no card — fundo claro com borda suave, sem mais o destaque verde
- Cards de total/pendente em Lançamentos redesenhados: sem caixas ("cards"), texto limpo ao lado do título, com uma barra de progresso fina no valor pendente de efetivação

## [1.3.1] - 2026-08-09

### Added
- Cards de total e "pendente de efetivação" ao lado do título na tela de Lançamentos, refletindo o filtro atual
- Card "Metas em aberto" no Dashboard, ao lado do Orçamento do mês, com barra de progresso por meta e atalho direto para a tela de Metas
- Extrato de movimentos (entrada/saída, com data) dentro do modal de atualizar progresso de uma Meta
- Botão "Meta alcançada" ao editar uma meta, para marcar como concluída manualmente

### Changed
- Despesas agora ordenadas pela data de **vencimento** em Lançamentos e extratos — despesas de cartão usam a data de pagamento da fatura, não a data da compra
- Dashboard reorganizado: "Comparativo com o mês anterior" ao lado de "Top categorias"; "Orçamento do mês" ao lado do novo card de Metas
- Modal "Atualizar progresso" da Meta redesenhado: título no padrão do sistema (negrito + ícone + nome), toggle Entrada/Saída na mesma linha do valor, e o valor passou a representar um lançamento (que soma ou subtrai do progresso) em vez de um valor absoluto
- Layout de "Nova Meta" corrigido para o padrão do sistema (ícone + nome + cor na mesma linha)
- Botão "Atualizar progresso" destacado nos cards de Meta
- Subtítulos de Metas e Tags simplificados

### Fixed
- **Crítico:** ao trocar entre "Entrada" e "Saída" no modal de atualizar progresso de uma meta, o valor já digitado era apagado — corrigido para que a troca de tipo não afete mais o valor no campo

## [1.3.0] - 2026-08-08

### Added
- **Metas financeiras**: nova tela independente para criar objetivos (ex: "Viagem — R$5.000 até dezembro"), com ícone, cor, valor alvo, data alvo opcional, barra de progresso e atualização manual do valor acumulado. Não interfere em orçamento, investimentos ou lançamentos — é um controle totalmente separado
- Botão de reconexão em um clique na tela inicial, que aparece automaticamente quando há um arquivo de dados lembrado de uma sessão anterior
- Indicador visual de "Salvando..." no rodapé do menu lateral enquanto o app grava no arquivo
- Data de término opcional para lançamentos com recorrência "Fixo mensal" — útil para gastos fixos com prazo certo, como financiamentos
- Card de comparativo "este mês vs. mês passado" no Dashboard, mostrando as categorias de despesa com maior variação

### Changed
- Reconexão automática ao arquivo anterior agora é assistida por um botão dedicado, já que navegadores não permitem pedir permissão de arquivo sem uma ação direta do usuário

## [1.2.7] - 2026-08-05

### Fixed
- **Crítico:** aportes lançados no mesmo dia de uma atualização de valor já existente não somavam ao "Valor Total" do ativo. A causa era que o sistema comparava apenas a data (dia inteiro) entre aportes e atualizações, sem saber qual dos dois eventos realmente aconteceu primeiro — e assumia sempre que o aporte já estava embutido no valor digitado na atualização, mesmo quando não estava.
  - Corrigido guardando o horário exato de criação (interno, não visível na interface) de cada aporte e atualização de valor, permitindo ao sistema reconstruir a ordem real dos eventos dentro do mesmo dia.
  - Validado com o cenário real reportado: uma atualização de R$7.145,99 já registrada, seguida de um aporte de R$10,71 lançado depois no mesmo dia — antes o Valor Total ficava travado em R$7.145,99, agora soma corretamente para R$7.156,70.
  - Testado também o cenário inverso (aporte lançado primeiro, atualização registrada depois já refletindo o aporte) para garantir que a correção anterior do cálculo de rendimento continua funcionando sem regressão.
  - **Observação:** essa correção vale para lançamentos feitos a partir de agora. Aportes e atualizações já existentes no seu arquivo não têm esse horário de criação salvo e podem, no primeiro carregamento após a atualização, ainda apresentar a inconsistência em casos específicos de mesmo dia — editar e resalvar esses registros resolve.

## [1.2.6] - 2026-08-05

### Added
- Detalhamento do Saldo Previsto agora inclui os aportes de investimento pendentes que já têm conta de origem definida, com uma lista detalhada acessível por clique

### Changed
- Coluna "Categoria" na lista de Investimentos revertida para largura automática (sem tamanho fixo)
- "Saldo Inicial" do Dashboard agora considera despesas já vencidas e ainda não marcadas como pagas (normais e de cartão, usando a data de vencimento da fatura) como já debitadas na projeção do saldo — deixando mais realista o ponto de partida do mês

### Investigated
- Reportado que aportes não estariam somando ao "Patrimônio Atual" em alguns testes — não foi possível reproduzir em testes extensivos (criação nova e fluxo completo pela tela). Aguardando mais detalhes do cenário para investigação direcionada.

## [1.2.5] - 2026-08-04

### Added
- Aba "Investimento" no card de Orçamento do Dashboard, ao lado de Entrada e Despesa
- Card de alerta para faturas de cartão vencendo em até 3 dias ou vencidas, no mesmo padrão dos alertas de despesas/entradas/transferências — abre a fatura diretamente quando há só uma pendente, ou uma lista quando há mais de uma

### Changed
- Coluna "Categoria" na lista de Investimentos com largura padrão fixa; texto muito longo agora quebra linha em vez de esticar a tabela
- Card "Resultado do mês" no Dashboard passa a descontar também os aportes de investimento efetivados no mês, não só as despesas

### Fixed
- **Crítico:** o rótulo "Saldo Previsto" no Dashboard ficava desalinhado em relação ao valor abaixo dele — a causa era a mudança para exibir o ícone de detalhamento, que quebrou a centralização automática do card. Corrigido explicitando o alinhamento central

## [1.2.4] - 2026-08-04

### Added
- 3 novas cores vívidas no seletor (verde, turquesa e magenta), totalizando 16 opções organizadas em ordem de matiz (vermelhos → laranjas → amarelos → verdes → azuis → roxos → rosa → neutros)

### Changed
- Seletor de cores reorganizado para exibir 8 opções por linha (antes 6), com popover mais largo para acomodar o novo layout
- Orçamento de investimento não entra mais na dedução do Saldo Previsto quando não há aporte vinculado a uma conta — ele só afeta a previsão quando o aporte de fato tem uma conta de origem definida
- Modal "Como chegamos no Saldo Previsto" atualizado: a seção de orçamento restante agora mostra só despesas (investimentos removidos), com uma nota explicando o motivo

### Fixed
- **Crítico:** identificada a causa raiz do bug de rendimento que persistia desde versões anteriores — quando um aporte e uma atualização de valor aconteciam no **mesmo dia** (cenário comum no uso real), o sistema não incluía esse aporte na base de cálculo do rendimento, fazendo o valor aportado aparecer quase inteiro como "rendimento". Corrigido em todos os pontos do sistema que calculam rendimento: cards da tela de Investimentos, linhas de rendimento na aba Investimentos de Lançamentos, extrato do ativo, e rentabilidade (1 mês / 3 meses / total-ano). Testado com o cenário exato reportado: rendimento que aparecia como R$2.311,60 (quase todo aporte) agora mostra corretamente R$7,55, batendo exatamente com a soma saldo inicial + aportado + rendimento = valor total
- Saldo Previsto do Dashboard estava descontando duas vezes o valor de orçamentos de investimento sem conta vinculada

## [1.2.3] - 2026-08-03

### Added
- Detalhamento do Saldo Previsto no Dashboard: um ícone ao lado do valor abre um modal explicando a composição (entradas previstas, despesas previstas, restante do orçamento por categoria), com cada linha navegável até a lista completa
- Nova cor vívida (#E0562E) no conjunto de cores predefinidas para categorias, contas e cartões

### Changed
- Filtro de Lançamentos invertido: agora oculta os itens efetivados quando ativado (em vez de mostrar só os efetivados), desligado por padrão
- Círculo de efetivação travado na fatura de cartão: borda no padrão visual das demais, fundo cinza mais escuro
- Cards da tela de Investimentos reordenados — "Patrimônio Atual" (antes "Patrimônio Total") movido para depois de "Rendimento no mês"; "Saldo inicial do mês" renomeado para "Patrimônio inicial do mês"
- Orçamento de investimento: só conta como "realizado" no desconto do Saldo Previsto quando o aporte teve uma conta de origem — aportes sem conta vinculada não afetam mais essa previsão

### Fixed
- **Crítico:** a aba "Investimentos" da tela de Lançamentos calculava o rendimento do mês pela diferença bruta entre duas atualizações de valor consecutivas, o que incluía qualquer aporte feito no meio do período — inflando o rendimento exibido tanto nas linhas quanto nos totais. Corrigido para usar a mesma lógica já validada em outras partes do sistema, que isola corretamente o ganho de mercado do valor aportado. Testado com um cenário de 3 meses (rendimento, aporte, rendimento): cada mês agora mostra o valor exato, sem mistura

## [1.2.2] - 2026-08-03

### Added
- Orçamento de investimento: ao criar um orçamento na aba Investimentos, não é mais necessário escolher categoria — apenas valor planejado e "válido a partir de". O realizado soma automaticamente todos os aportes do mês e desconta do Saldo Previsto do Dashboard
- Card "Saldo inicial do mês" na tela de Investimentos, mostrando o patrimônio antes de qualquer rendimento ou aporte do mês corrente

### Changed
- Filtro "Só efetivados" em Lançamentos agora usa um switch de verdade (liga/desliga), em vez de um botão colorido
- Removidos da tela de Fatura os ícones de "mover lançamento para outra fatura" e de efetivação manual — o pagamento de cartão continua sendo controlado exclusivamente pelo botão "Pagar Fatura"

### Fixed
- **Crítico:** as colunas "1 mês", "3 meses" e "Total/ano" da tela de Investimentos calculavam a rentabilidade pela diferença bruta de saldo, o que incluía aportes feitos no período — inflando o percentual mostrado. Corrigido para considerar apenas o rendimento real (ganho de mercado), excluindo o valor principal injetado por aportes. Testado com um cenário controlado: rentabilidade que antes apareceria como ~65% (incluindo um aporte) agora mostra corretamente 15% (só o rendimento)

### Pending confirmation
- Aguardando definição sobre a "data de efetivação" dos lançamentos (unificar com a data de vencimento vs. manter oculta/automática) e sobre o formato do detalhamento do Saldo Previsto no Dashboard — propostas apresentadas, implementação represada até confirmação.

## [1.2.1] - 2026-08-03

### Added
- Círculo de efetivar direto na lista de pendências do Dashboard, permitindo marcar despesas/entradas/transferências como resolvidas sem abrir o lançamento
- Filtro "Só efetivados" (on/off) na tela de Lançamentos, ao lado dos demais filtros
- Ícone de pílula/remédio para categorias

### Changed
- Cards de pendências do Dashboard reordenados: Entradas → Despesas → Transferências, agora com cor fixa por tipo (verde, vermelho, amarelo) em vez de cor por urgência
- Campo "Debitar da conta" / "Creditar na conta" no lançamento de Aporte agora mostra o círculo colorido e o ícone do banco, no mesmo padrão usado nos outros seletores de conta do sistema
- Campo "Conta vinculada" ao editar um cartão também passou a mostrar círculo colorido + ícone do banco

### Fixed
- **Crítico:** lançar um aporte selecionando a conta de débito criava automaticamente uma despesa duplicando o efeito no saldo — removida essa criação automática; o aporte já debita o saldo da conta diretamente e aparece normalmente na lista de aportes do mês, sem gerar um lançamento de despesa

## [1.2.0] - 2026-08-03 (atualização)

### Added
- Cards de pendências para Entradas e Transferências no Dashboard, seguindo o mesmo padrão já existente para Despesas — cada um mostra a contagem de itens vencidos, vencendo hoje ou nos próximos 3 dias
- Os três cards de pendências (Despesas, Entradas, Transferências) agora aparecem lado a lado quando há mais de um tipo pendente
- Modal de pendências generalizado para os três tipos: título, cor do valor (verde para entrada, vermelho para despesa/transferência) e o texto do botão de resolver ("Marcar como paga" / "Marcar como recebida" / "Marcar como concluída") se ajustam automaticamente ao tipo

### Fixed
- Pequeno erro de concordância no texto dos cards de pendência ("1 despesa precisam" → "1 despesa precisa")

## [1.1.9] - 2026-07-31

### Added
- 4 novos ícones de categoria: cama, muro, ônibus e chave de boca
- Consolidação "Demais categorias" no Top Categorias do Dashboard: mostra apenas as 4 categorias com maior gasto, somando o restante em uma única fatia
- Porcentagem exibida ao lado do nome de cada categoria na legenda do Top Categorias
- Campo de fuso horário em Configurações > Personalização, com -03:00 (Brasília) como padrão

### Changed
- Listas de Categorias e de Orçamento agora ordenadas alfabeticamente
- Subtítulo do Dashboard fixo em "Visão financeira mensal consolidada", sem mês/ano
- Modal de Editar Orçamento reorganizado: categoria e subcategoria na mesma linha; valor planejado e "válido a partir de" na mesma linha
- Proporção dos cards do Dashboard ajustada: "Orçamento do mês" maior, "Top categorias" menor
- Navegador de mês da tela de Fatura centralizado, com o total permanecendo fixo à direita

### Fixed
- **Crítico:** editar um lançamento que já era a última parcela de uma série finalizada (ex: 6/6) gerava parcelas extras incorretas (7/6, 8/6...) — a causa era uma condição de reprocessamento de parcelamento disparando indevidamente em edições comuns de itens já processados; a lógica foi simplificada e agora só reprocessa em criações novas, ativações genuínas ou reset explícito dentro da mesma sessão

## [1.1.8] - 2026-07-31

### Added
- 3 novos ícones de categoria: peso de academia, avião e bola
- Porcentagem exibida ao lado do nome de cada categoria na legenda do Top Categorias (Dashboard)
- Barra de rolagem no seletor de ícones de categoria, com abertura automática para cima quando não há espaço abaixo

### Changed
- Campo de busca em Lançamentos com altura levemente maior
- Título do extrato aberto por uma categoria do Dashboard agora inclui o ícone da categoria
- Botão de arquivar categoria trocado para o símbolo de caixa, em tom discreto
- Subtítulo da tela de Orçamento sem o mês ("Planejamento por categoria")
- Aba de Categorias abre por padrão em "Entradas"
- Ícones "pizza" e "abstract" removidos do seletor de categorias (substituídos com segurança em todos os locais que os usavam)
- Barra de progresso do total do orçamento agora muda de cor conforme o avanço: amarelo a partir de 70%, laranja a partir de 90%, vermelho a partir de 100%
- Tela "Sobre o Dolfin" reposicionada para abaixo do card de Personalização nas Configurações
- Removido o travessão antes do valor total no painel de detalhe do Top Categorias
- Modal de Fatura e de extrato por categoria: total fixo no topo, ao lado do navegador de mês; apenas a lista de lançamentos rola, o cabeçalho permanece visível

### Fixed
- **Crítico:** despesas de cartão passavam a ficar "efetivadas" automaticamente quando lançadas com data igual ou anterior a hoje — agora permanecem sempre não efetivadas até o pagamento da fatura, independente da data
- **Crítico:** ao selecionar uma sugestão de lançamento antigo no autocomplete do campo Nome, o novo lançamento herdava a recorrência e o mês de fatura do lançamento original — agora sempre volta ao padrão (sem recorrência, fatura recalculada do zero)
- **Crítico:** ao desfazer o parcelamento de um lançamento e parcelar novamente, o nome acumulava sufixos duplicados (ex: "Nome (2/5) (2/5)") — corrigido removendo um bloco de código redundante que processava o sufixo duas vezes
- Desativar a recorrência de um lançamento agora reseta todos os campos dela (parcelas, intervalo, período) para o padrão, para que reativar comece do zero em vez de manter valores antigos
- Subcategoria "Outros" agora exibe o ícone da categoria-pai (em vez do ícone genérico) nas listas de Lançamentos, extrato de conta e fatura

## [1.1.7] - 2026-07-31

### Added
- Ícones adicionais no seletor de categorias: 3 de dinheiro/investimento (moeda, cofrinho, carteira) e 3 de lazer (jogo, praia, câmera)
- Preferência de ordenação em Configurações > Personalização (mais novo → mais antigo, ativado por padrão), aplicada em Lançamentos, Investimentos, extrato por categoria, extrato de conta, fatura e extrato do ativo
- Link "Sobre" diretamente no sidebar, abaixo de "Configurações"
- Tamanho de página padrão da lista de Lançamentos (10 itens) salvo na base, respeitado a cada abertura

### Changed
- Campo de busca em Lançamentos com altura e fonte reduzidas
- Rótulo do campo de data no lançamento alterado para "Data e hora"
- Título do extrato ao clicar em uma categoria no Dashboard: "**Despesas:** Categoria - Mês" (negrito + peso normal)
- Fonte normal (sem negrito) na lista de Categorias
- Abas de Categorias reordenadas para Entradas / Despesas / Investimentos
- Menu de três pontinhos removido da lista de Categorias — ícones diretos de arquivar e excluir em cada linha
- Subtítulo da tela de Investimentos sem o mês ("Carteira, aportes e rentabilidade")
- Botão "Atualizar valor" no extrato do ativo com borda mais escura
- Título do extrato do ativo no mesmo padrão visual dos demais ("**Extrato:**" em negrito + resto em peso normal)
- Orçamento: texto "estourado" removido; ultrapassar 100% só é destacado em vermelho para despesas — para entradas, ultrapassar a meta é positivo e não é mais destacado em vermelho

### Fixed
- **Crítico:** ao selecionar uma sugestão de lançamento antigo já efetivado no autocomplete do campo Nome, o novo lançamento vinha com a data e o status de efetivação daquele lançamento antigo — agora sempre reseta para o padrão de um lançamento novo (data de hoje, efetivado conforme a regra normal)
- Botão "Sobre" não aparecia como link direto no sidebar, apenas dentro do conteúdo de Configurações

## [1.1.5] - 2026-07-30

### Added
- Modal "Pagar Fatura": campo de valor pago (pré-preenchido com o total) e data do pagamento, na mesma linha
- Pagamento parcial da fatura: o valor restante é automaticamente transferido como um novo lançamento para a próxima fatura
- Botão "Reabrir a fatura" para desfazer um pagamento (total ou parcial), com destaque visual (vermelho)
- Navegação de mês (‹ Mês/Ano ›) independente dentro do modal de Fatura e também no Extrato de Conta
- Campo "Recorrência" unificado num único controle (ícone + resumo + popover), com select nativo (Não recorrente / Parcelado / Fixo mensal); os campos de parcela (parcela inicial, nº de parcelas, período, valor total/parcela) só aparecem ao escolher "Parcelado"
- Suporte a período de parcelamento em "Dia(s) / Mês(es) / Ano(s)" com intervalo customizável (ex: "a cada 13 dias")
- Ao editar um lançamento parcelado, pergunta se a alteração vale só para aquela ocorrência ou para toda a série
- Ao desativar a recorrência de um lançamento já existente, pergunta se as outras ocorrências da série devem ser excluídas também
- Orçamento: opção de excluir diretamente na tela de edição, além da lista
- Orçamento: editar o valor pergunta se a mudança vale só para o mês selecionado ou daquele mês em diante (histórico de valores por mês)
- KPI "Rendimento no mês" (em R$) na tela de extrato do próprio ativo
- Botão "Sobre o Dolfin" nas Configurações

### Changed
- Título da Fatura, do "Pagar Fatura" e do Extrato de Conta seguem o mesmo padrão visual ("Rótulo:" em negrito + ícone/nome em peso normal), com espaçamento reduzido
- Status "Aberta" em azul (antes amarelo); fatura paga mostra "Fatura Paga"
- Dashboard: valor da fatura alinhado à direita com o mês (ex: "ago/26") antes do valor; linha de baixo mudou para "Próxima fatura: R$X"
- Barras de progresso do orçamento (Dashboard): comprimento padronizado entre categorias, percentual mais próximo do final da barra, cor da categoria em cada linha e cor por tipo (verde/vermelho) na barra de total; percentual do total sem negrito
- Orçamento: clicar na linha abre direto a edição (antes abria a categoria por engano); menu de 3 pontinhos removido, ícone de excluir direto na linha
- Novo lançamento: "Efetivado" liga/desliga automaticamente conforme a data seja passada/hoje ou futura, mas continua editável manualmente

### Fixed
- **Crítico:** categoria não vinha pré-selecionada em novos lançamentos — a causa raiz era que a memória da "última categoria usada" só existia na sessão do navegador e se perdia a cada recarregamento; agora é salva no arquivo junto com os demais dados
- **Crítico:** status "Fatura Paga" não atualizava (e o botão de reabrir não aparecia) quando uma fatura de mês futuro era paga antecipadamente — a verificação de status checava primeiro se o período de fechamento já tinha passado, ignorando se a fatura já estava paga
- **Crítico:** saldo da conta e os extratos consideravam a data original do lançamento em vez da data de efetivação — ampliado para todos os lançamentos (não só cartão): uma despesa só afeta o saldo e aparece no extrato do mês em que foi de fato efetivada
- **Crítico:** ao alterar o número de parcelas de uma série já criada, o sistema só reescrevia o texto "(X/Y)" nas parcelas existentes — aumentar a quantidade não criava as parcelas que faltavam, e diminuir não removia as excedentes (protegendo as já pagas)
- **Crítico:** ao aplicar uma edição para "todas as ocorrências" de uma série parcelada, a competência da fatura de uma parcela estava sendo copiada para todas as outras, jogando tudo na mesma fatura
- Popover de recorrência abria sozinho ao editar um lançamento parcelado já existente, causando comportamento inconsistente
- Rendimento da primeira atualização de valor de um ativo não era somado ao "Rendimento no mês" (só a partir da segunda atualização)
- KPI "Rentabilidade média" do Dashboard substituído por "Rentabilidade no mês", alinhado com o mesmo cálculo da tela de Investimentos

## [1.1.3] - 2026-07-29 16:00

### Added
- Linha de "Total" ao final de cada grupo de conta na tela de Investimentos, somando os campos em valor monetário (Saldo início do mês, Aportado no mês, Rendimento no mês e Valor total)
- Barra de progresso no quadro "Orçamento do mês" do Dashboard entre "Total Entradas/Despesas" e o valor, nas cores por tipo (verde para Entrada, vermelho para Despesa)

### Changed
- Barra de progresso de cada categoria no quadro de orçamento do Dashboard: na mesma linha do nome, entre o nome e o valor total/consumido, usando a cor da própria categoria
- Linha de "adicionar nova subcategoria": ícone, cor e campo de texto alinhados no meio, com a cor logo após o campo de texto
- Menu de ações do ativo simplificado para apenas "Transferir ativo", "Editar" e "Excluir"
- "Novo Aporte": campo "Categoria de Investimento" removido; campo "Ativo" agora mostra ícone + conta + nome do ativo (ex: "Nubank - CDI")
- Extrato do ativo: título agora mostra ícone + banco + nome do ativo (ex: "Extrato: Nubank - CDI")
- Campo "Válido a partir de" do orçamento passa a usar como padrão o mês que está sendo visualizado no app, não a data real do sistema

### Fixed
- **Crítico:** saldo inicial do ativo estava sendo somado como aporte no "Total Aportado"; e quando o ativo não tinha nenhuma atualização de valor, "Valor Atual" ficava zerado em vez de refletir o saldo inicial
- **Crítico:** "Patrimônio Total" passou a considerar apenas ativos já existentes no mês em questão — um ativo criado em agosto não aparece mais retroativamente no patrimônio de meses anteriores
- **Crítico:** despesas de cartão ainda não pagas, mas presentes na fatura do mês, não estavam sendo contabilizadas no "Realizado" dos orçamentos de despesa
- Orçamento recorrente estava projetando o valor "restante" (ainda não gasto) em todos os meses futuros indefinidamente, mesmo sem nenhuma despesa real agendada — corrigido para respeitar apenas o mês configurado em "Válido a partir de"

## [1.1.2] - 2026-07-29 11:00

### Added
- Linha de "Total" ao final de cada grupo de conta na tela de Investimentos, somando os campos em valor monetário (Saldo início do mês, Aportado no mês, Rendimento no mês e Valor total) de todos os ativos daquela conta

### Fixed
- **Crítico:** o saldo inicial do ativo estava sendo somado como se fosse um aporte no "Total Aportado", e quando o ativo não tinha nenhuma atualização de valor registrada, o "Valor Atual" e o "Valor Total" da lista ficavam zerados em vez de refletir o saldo inicial. Corrigido: agora "Total Aportado" conta só aportes reais, e "Valor Atual"/"Valor Total" usam o saldo inicial como base quando ainda não há atualização de valor — refletindo corretamente em toda a tela de Investimentos (lista, extrato do ativo e Patrimônio Total)

## [1.1.1] - 2026-07-29 09:00

### Added
- Saldo inicial do ativo passa a aparecer como uma linha própria ("Saldo inicial") no extrato do investimento, com opção de editar
- Opção "Transferir para outro ativo" nos investimentos (aporte/resgate vinculados, sem afetar conta bancária)
- Selo verde ("orelha") no canto superior esquerdo dos cards de conta/cartão marcados como padrão
- "Top categorias de despesa" no Dashboard virou um gráfico de rosca (donut) interativo: 5 maiores categorias + "Outros" agregado, com legenda e detalhe (valor + %) ao clicar em cada fatia
- KPIs "Receitas efetivadas" e "Despesas efetivadas" do Dashboard agora são clicáveis e abrem um extrato dos lançamentos daquele mês
- Botões de Aporte, Resgate e Atualizar valor no extrato do ativo modernizados com ícone e cor (verde/vermelho/neutro)

### Changed
- Título da aba do navegador simplificado para "Dolfin"
- Botão "É despesa de cartão?" movido para logo após a pergunta (não mais no extremo direito)
- Coluna "Conta" renomeada para "Conta/Cartão"
- Botão "+" volta a abrir por padrão na aba Entrada
- "Corrente" renomeado para "Conta Corrente" na coluna de conta/cartão
- Texto do campo de subcategoria no orçamento simplificado
- Aba "Investimentos" movida para depois de "Transferências" na tela de Lançamentos
- Coluna "Subcategoria" removida da tela de Lançamentos — consolidada dentro da própria coluna "Categoria" (formato "Categoria › Subcategoria")
- Tela de editar categoria: ícone da subcategoria alinhado de forma neutra à esquerda, com a cor movida para o final da linha (antes dos botões de editar/arquivar/excluir)
- Coluna "Ativo" da tela de Investimentos com largura fixa

### Fixed
- Linhas de lançamento e fatura de cartão não ficam mais acinzentadas — mantêm o mesmo aspecto visual das linhas comuns; apenas o círculo de efetivar sinaliza o status (cinza quando pendente, verde quando pago)
- **Crítico:** modal de "Novo Ativo" apagava o nome e o saldo inicial digitados ao trocar a categoria — faltava sincronizar os campos antes de redesenhar a tela
- **Crítico:** "Valor Total" na tela de Investimentos mostrava valores quase zerados mesmo para ativos com histórico acumulado de milhares de reais — a causa era conceitual: o valor total estava sendo calculado como a soma apenas dos 3 campos do mês corrente (saldo início + aportado + rendimento), que fica corretamente zerado quando o histórico do ativo é anterior ao mês em questão. Agora "Valor Total" volta a refletir o valor acumulado real (mesma fonte usada no KPI "Patrimônio Total"), enquanto os 3 campos do mês continuam servindo só como detalhamento informativo

## [1.1.0] - 2026-07-28 18:00

### Added

#### Lançamentos
- Abas (Entrada / Despesa / Transferência) dentro do próprio modal de lançamento, substituindo o menu "alterar tipo" escondido no kebab
- Botão "+" agora abre direto na tela de Despesa
- Coluna Conta/Cartão redesenhada em duas linhas: tipo da conta ("Corrente", "Poupança"...) ou "Cartão de Crédito" na primeira linha, ícone + nome na segunda

#### Dashboard
- KPIs de Receitas, Despesas e Resultado do mês agora mostram o valor efetivado e o previsto
- KPI "Investido no mês" com percentual sobre o total de receitas
- "Top categorias de despesa" passa a incluir despesas lançadas mesmo que ainda não efetivadas
- Clique no cartão do Dashboard abre a fatura no mês correto (a mesma exibida no card), com opção de reabrir faturas já fechadas dentro do próprio modal

#### Investimentos
- Opção "Transferir para outro ativo" (cria um resgate e um aporte vinculados, sem afetar saldo de conta)
- Campo de saldo inicial no ativo, para ajustes manuais quando necessário
- Os 4 KPIs (Aportado, Patrimônio, Rendimento, Rentabilidade) agrupados em uma única linha

### Changed
- "É despesa de cartão?" volta sempre desligado por padrão ao criar uma nova despesa — precisa ser habilitado manualmente
- Linhas da fatura do cartão voltam a ser clicáveis para edição completa do lançamento; apenas o botão de efetivar continua bloqueado (só é possível efetivar pagando a fatura)
- "Ver extrato" removido do menu de ações do ativo (redundante com o clique na linha)
- Lançamento do tipo "Investimento" não é mais criado pela tela de Lançamentos — toda movimentação de investimento passa a ser feita exclusivamente pela tela de Investimentos

### Fixed
- **Crítico:** menu de ações (⋮) cortado/inacessível quando o botão estava perto do fim da página — o menu sempre abria para baixo sem checar se cabia na tela; agora inverte para cima quando necessário
- Botão "+" quebrando o aplicativo inteiro após ajuste anterior no código (chave sobrando)


## [1.0.2] - 2026-07-28 10:00

### Added

#### Lançamentos
- Toggle "É despesa de cartão?" (após a Descrição) — ao ativar, sugere automaticamente o cartão e a conta padrão/preferencial e a competência da fatura já aberta
- Combo de mês/ano da fatura, permitindo escolher em qual competência a despesa de cartão deve cair
- Campo de hora ao lado da data combinados na exibição ("Data/Hora") em listas e extratos
- Autocomplete de categoria/subcategoria: pré-seleciona a última combinação usada por tipo (Entrada/Despesa/Investimento)
- Subcategoria "Outros" pré-selecionada automaticamente ao escolher a categoria
- Calculadora embutida no campo Valor
- Validação de campos obrigatórios com asterisco, destaque do campo com erro e rolagem automática até ele
- Exclusão de lançamento recorrente/parcelado agora pergunta: somente esta ocorrência, esta e as futuras, ou todas as ocorrências da série
- Indicação visual (cinza = pendente, verde = paga) para despesas vinculadas a cartão; o botão de efetivar fica travado nelas — só é possível efetivar pagando a fatura
- Tags: campo de busca embutido no próprio botão, com opção de criar a tag na hora

#### Contas e Cartões
- Toggle "Conta padrão" e "Cartão padrão", usados para sugestão automática em novos lançamentos
- Toggle "Ocultar esta conta da tela principal"
- Sistema de arquivamento de contas e categorias/subcategorias, com seção "Ver arquivadas" e opção de restaurar
- Alerta "Pagar até DD/MM" no Dashboard e na tela de Cartões quando a fatura fechou e ainda há lançamento pendente
- Modal de fatura: navegação de mês independente (‹ Mês/Ano ›), status "Paga" com opção de reabrir, coluna de categoria mostrando categoria › subcategoria com ícone

#### Orçamento
- Opção de orçar uma subcategoria específica (além da categoria inteira)
- Campo "Válido a partir de" como seletor de mês/ano
- Percentual da barra de progresso agora na mesma linha, ao final

#### Investimentos
- Tela reorganizada com os ativos agrupados por conta associada
- Novo KPI "Rentabilidade no mês"
- Colunas de rentabilidade de 1 mês e 3 meses por ativo
- Aporte e resgate com o mesmo campo de tags (busca + criação embutida) da tela de lançamentos
- Aportes, resgates e rendimentos agora aparecem na aba "Investimentos" da tela de Lançamentos
- Novo ícone de medicamento e mais 4 ícones de alimentação (pizza, café, hambúrguer, maçã) e 4 de saúde (hospital, estetoscópio, dental, fitness)

#### Dashboard
- Clicar no mês no topo volta para o mês atual (hoje)
- Quando a fatura de um cartão já foi paga, o card do Dashboard passa a mostrar a próxima fatura em aberto como valor principal, com rótulo sutil do mês (ex: "Jul/26") e a prévia do mês seguinte
- Contas com "Previsto" diferente de zero não somem mais mesmo com saldo efetivado zerado (opção "mostrar apenas contas com saldo")

### Changed
- Saldo das contas: valor principal agora só soma lançamentos efetivados; "Previsto" exibido como informação secundária, discreta, considerando apenas o mês vigente (sem acumular previstos de meses anteriores)
- Despesa de cartão só afeta o saldo previsto da conta no mês do **vencimento** da fatura, não no mês da compra
- Parcelamento: opções padrão agora vêm como "Total" e "Parcelado" (antes "Parcela" e "Fixo")
- Ícones de conta/cartão com cor de contraste automática (branco em fundo escuro, escuro em fundo claro)
- Categoria de investimento (antes um texto livre "tipo") migrada para categorias de verdade, com migração automática dos valores antigos

### Fixed
- **Crítico:** não era possível salvar nenhuma despesa — o código tentava ler o campo do cartão mesmo quando ele não existia no formulário (toggle desligado), quebrando o salvamento silenciosamente
- **Crítico:** parcelamento sempre limitado a 2 parcelas e duplicando o nome/valor ao editar — o cálculo de parcelamento era reaplicado a cada salvamento em vez de só na criação
- **Crítico:** aporte não somava ao valor atual do ativo quando já havia uma atualização de valor registrada — agora aportes feitos após a última atualização são somados corretamente
- Rentabilidade de investimento mostrando percentuais absurdos (600.000%+) — recalculada com base na variação de valor de mercado, não mais dependente do total aportado
- Ícones desproporcionais (gigantes) em: criação de tags, ícone de recorrência na lista, botão "+ nova categoria" do ativo — causa raiz era a falta de uma regra de CSS restringindo o SVG dentro do elemento wrapper
- Categorias "Outros" sendo criadas indevidamente para Investimento (categoria de nível único) — migração corrigida e limpeza automática das subcategorias incorretas
- Asterisco de campo obrigatório quebrando o layout (aparecia na linha de baixo) — causa raiz era o texto solto e o `<span>` do asterisco virando itens de flexbox separados
- Cor da fonte inconsistente entre data e hora nos extratos
- Contagem de "Top categorias de despesa" duplicada (somava categoria e subcategoria ao mesmo tempo)

## [1.0.1] - 2026-07-25 12:00

### Added

#### Geral / Sistema
- Paleta de cores expandida: variações clara/principal/escura agrupadas por matiz em todos os seletores de cor
- Botão de cor migrado para um seletor circular (popover), menor e ao lado do campo Nome
- Seletor de ícone com preview + popover de escolha (ícones limpos, monocromáticos, com mapeamento de migração dos emojis antigos)
- Ícone abstrato neutro como padrão para novas categorias
- Novo pack de ícones de serviços (wifi, água, energia, streaming, assinatura) e de saúde (coração)
- Cor de contraste automática nos ícones circulares (branco em fundo escuro, escuro em fundo claro) — Dashboard, Contas, Cartões
- Menu kebab (⋮) genérico reutilizável em Contas, Cartões, Categorias, Orçamento e Investimentos
- Componente de "select customizado" (botão colorido + popover) para Conta, Cartão, Categoria e Subcategoria
- Calculadora embutida no campo Valor do lançamento
- Validação de campos obrigatórios (Nome, Data, Valor, Conta, Categoria, Subcategoria) com asterisco, destaque visual e rolagem automática até o campo com erro
- Favicon com fundo verde e golfinho dourado

#### Sidebar
- Logo do golfinho e nome "Dolfin" centralizados e mais próximos; "Finanças Pessoais" reaproximado
- Configurações movida para o rodapé do sidebar, acima do Desconectar
- Botão Desconectar com fundo vermelho claro

#### Configurações
- Nova seção "Arquivo base" (Salvar agora / Carregar outro arquivo / Desconectar)
- Toggle "Orçamento afeta o saldo previsto"
- Toggle "Mostrar apenas contas com saldo"

#### Categorias
- Conceito de subcategoria via "+" contextual (categoria-pai não é mais selecionável em dropdown)
- Categoria "Outros" (cinza) criada automaticamente em toda nova categoria de nível 1
- Subcategoria herda a cor da categoria-pai por padrão
- Abas por tipo (Despesas / Entradas / Investimentos)
- Edição de categoria já permite incluir, editar, arquivar ou excluir subcategorias na mesma tela
- Sistema de arquivamento com restauração (Contas, Categorias e Subcategorias)

#### Contas
- Ícone por tipo de conta (banco / cofrinho / carteira / gráfico), com seletor de ícone
- Conta "Carteira" criada automaticamente (com ícone) ao gerar um arquivo novo
- Campo de moeda principal por conta (BRL / USD / EUR / GBP / MXN)
- Extrato unificado por conta (clique no card abre modal com todos os lançamentos e status)
- Toggle "Ocultar esta conta da tela principal"
- Menu kebab (Ver extrato / Editar / Arquivar / Excluir definitivamente)

#### Cartões
- Ícone de cartão (schema + seletor)
- Fatura em modal com a mesma visão da tela de Lançamentos (linhas clicáveis, botão de efetivar embutido)
- Botão "Marcar fatura como paga" — efetiva todas as despesas da fatura na data de vencimento
- Campo de competência por despesa, permitindo jogar uma despesa para outro mês de fatura
- Menu kebab (Ver extrato / Editar / Arquivar / Excluir definitivamente)

#### Lançamentos
- Abas por tipo (Entradas / Despesas / Investimentos / Transferências)
- Campo Nome (obrigatório) separado da Descrição (texto livre)
- Campo de hora ao lado da data, pré-preenchido com o horário de criação
- Categoria e Subcategoria obrigatórias, com seleção via lista customizada (ícone + cor)
- Parcelamento: sim/não, mensal/anual, valor total ou por parcela, fixo (até parar) ou número definido de parcelas — com geração automática das ocorrências
- Tipo "Investimento" (restrito a contas de investimento)
- Menu "..." consolidado: alterar tipo (submenu, exclui o tipo atual) + duplicar
- Botão de duplicar também na listagem
- Botão circular de "efetivado" com sinal de visto, direto na lista
- Tags via botão com popover de busca e criação embutida
- Categoria/Subcategoria pré-selecionadas com a última combinação usada, por tipo
- Regra: despesas vinculadas a cartão só ficam efetivadas quando a fatura é paga (não contam nos gastos do mês até lá)

#### Orçamento
- Categorias de Entrada, Despesa ou Investimento (antes só Despesa)
- Abas por tipo (Despesas / Entradas / Investimentos)
- Campo "Válido a partir de" — orçamento recorrente só passa a valer a partir do mês definido, sem afetar meses anteriores nem acumular
- Clique na linha abre a edição da categoria vinculada

#### Investimentos
- Tipo do ativo virou categoria de verdade (com migração automática dos tipos antigos: Renda Fixa, Ações etc.)
- Conta associada exibida na listagem
- Aporte e resgate podem debitar ou creditar diretamente uma conta do sistema
- Rendimento automático ao atualizar o valor de mercado (positivo ou negativo), ignorando a primeira atualização (que só define a base)
- Extrato por ativo (clique na linha) com histórico de aportes, resgates e rendimentos — cada um editável ou excluível
- Menu kebab (Ver extrato / Aporte / Resgate / Atualizar valor / Editar / Excluir)

#### Dashboard
- Contas e Cartões lado a lado, linhas maiores, círculo de ícone maior
- Saldo atual em destaque + saldo previsto discreto abaixo; ícone de "mais detalhes" (abre edição)
- Cartões: fatura atual + previsão do próximo mês
- Top categorias de despesa com a cor da própria categoria
- KPIs organizados em 3 colunas fixas

### Changed
- Botões "Nova categoria / conta / cartão" modernizados, mantendo o verde padrão do sistema
- Fonte voltou ao stack neutro do sistema (revertida a fonte estilizada usada em rodada anterior)
- Nome e valor sem negrito na tabela de lançamentos
- Coluna Status removida da tabela de lançamentos; coluna Subcategoria adicionada (na cor da categoria-pai)
- Transferência sem coluna de categoria; nome padrão "Transferência" quando salva em branco
- Filtro de categoria nos lançamentos virou botão com busca

### Fixed
- Cor do seletor "desconfigurada" — causa raiz: o CSS de `.field` só era aplicado a `<label>`, não a `<div>`
- Ícones do Dashboard aparecendo pretos — faltava a cor branca/contraste no CSS do círculo
- Campo Hora com tamanho desproporcional ao lado da Data — `input[type=time]` estava fora da regra base de estilo
- Valor negativo não ficava vermelho na tabela — classes `.neg`/`.pos` só existiam dentro de `.kpi-card`/`.ledger-node`, nunca como regra global
- `</div>` sobrando quebrava o layout do card de Conta (saldo vazando para fora do card)
- Ícone de "+" na criação de tag fora do tamanho padrão
- Contagem duplicada no "Top categorias de despesa" (somava categoria e subcategoria ao mesmo tempo)

### Removed
- Categoria de conta (feature revertida)
- "Alterar tipo" do menu de orçamento

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
