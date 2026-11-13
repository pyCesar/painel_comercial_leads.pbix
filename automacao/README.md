# Automação de alerta de leads incompletos (Make)
![Cenário no Make](make.png)

Cenário simples no Make que avisa por e-mail quando um lead novo entra na planilha com dados faltando.

## Como funciona

1. **Gatilho:** o Make observa uma planilha do Google Sheets (`leads_novos`) e detecta cada linha nova.
2. **Filtro:** se o lead estiver sem nome, sem origem ou sem vendedor, o fluxo continua. Se estiver completo, ele para ali.
3. **Ação:** o Make envia um e-mail pelo Gmail com o assunto "Lead com dados faltando", mostrando o nome, a origem e o vendedor que chegaram.

## Por que fiz isso

No projeto do painel, a limpeza de dados foi feita na mão, depois que os erros já estavam na planilha. Aqui a ideia é pegar o problema na entrada, assim que o lead é cadastrado.

## Como testei

- Adicionei um lead com a origem em branco e o e-mail de alerta chegou.
- Adicionei um lead completo e nenhum e-mail foi enviado.

## Limitações

- A coluna de valor da proposta não é verificada, porque vazio nela é um caso normal (proposta ainda sem valor).
- No plano gratuito, o Make verifica a planilha a cada 15 minutos.
- Os dados são fictícios.

## Arquivos

- `make.png`: print do cenário no Make
- `Integration Google Sheets, Gmail.blueprint.json`: arquivo exportado do cenário, que pode ser importado no Make
