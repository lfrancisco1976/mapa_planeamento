# Planeamento Logístico

Aplicação web estática para consulta de duas tabelas do ficheiro `MAPA PLANEAMENTO.xlsm`:

- Folha `Serv. pendentes`, tabela `mapa_planeamento6` (a linha de cabeçalhos está na linha 2 da folha).
- Folha `2026`, tabela `Tabela24247` (cabeçalhos na linha 1 da folha).

## Funcionalidades

- Vista de serviços pendentes.
- Vista de calendário diário de cargas, inicialmente posicionada na data atual, com navegação para o dia anterior/seguinte e botão Hoje.
- Filtros por data de carga (de/até), cliente, tipo de viatura, transportador e pesquisa livre.
- Detalhes adicionais por registo.
- Apenas leitura: a aplicação não altera o Excel.
- Tentativa de leitura automática do OneDrive e carregamento manual do `.xlsm` como alternativa.

## Publicar no GitHub Pages

1. Crie um repositório GitHub chamado, por exemplo, `planeamento-logistico`.
2. Carregue para a raiz do repositório os ficheiros `index.html` e `config.js`.
3. No repositório, abra **Settings → Pages**.
4. Em **Build and deployment**, escolha **Deploy from a branch**, selecione `main` e a pasta `/ (root)` e guarde.
5. Depois da publicação, abra o endereço apresentado pelo GitHub Pages (normalmente `https://NOME-DE-UTILIZADOR.github.io/planeamento-logistico/`).

## Ligação ao OneDrive e CORS

O endereço de partilha fornecido está configurado em `config.js`. A aplicação acrescenta `download=1` e tenta obter o Excel diretamente no navegador.

O SharePoint/OneDrive pode bloquear esta leitura por CORS, mesmo que o ficheiro esteja partilhado para qualquer pessoa com a ligação. Se isso acontecer, a aplicação apresenta a opção **Carregar Excel**. A leitura do ficheiro selecionado é feita localmente no navegador; o conteúdo do Excel não é enviado para o GitHub ou para outro servidor.

A biblioteca SheetJS é carregada a partir de jsDelivr, pelo que é necessária ligação à Internet para abrir a aplicação.

## Privacidade e acesso

O GitHub Pages é um alojamento público. Qualquer pessoa que conheça ou descubra o endereço da aplicação pode abrir a página. O link de partilha do OneDrive também permite acesso ao ficheiro a quem o possuir. Não publique esta aplicação com o link atual se os dados de clientes, operações, NEI, destinos ou transportadores não puderem ser consultados publicamente. O repositório contém apenas o código e a ligação partilhada; não contém uma cópia dos registos do Excel.

## Notas de interpretação

- A vista de pendentes apresenta os registos da tabela `mapa_planeamento6`, incluindo linhas sem data de carga e sem estado.
- A vista de calendário apresenta os registos da tabela `Tabela24247` na data de carga selecionada.
- Os estados são mostrados tal como estão no Excel. Um estado vazio é apresentado como **Sem estado**; a aplicação não assume que significa serviço realizado.
