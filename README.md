# Kerber Imóveis — Indicadores Comerciais

Painel diário comparativo para as equipes CANOAS, POA, POA ZS e VIAMÃO.

## Arquivos

- `index.html`: formulário de lançamento e quatro gráficos comparativos.
- `supabase/schema.sql`: tabela, validações e políticas de acesso do banco.

## 1. Configurar o Supabase

1. Crie um projeto em https://supabase.com/.
2. Abra **SQL Editor** e execute todo o conteúdo de `supabase/schema.sql`.
3. Em **Project Settings → API**, copie a **Project URL** e a chave **anon/public**.
4. No `index.html`, substitua `COLE_AQUI_A_URL_DO_PROJETO` e `COLE_AQUI_A_CHAVE_ANON_PUBLICA`.

Use somente a chave pública anon/publishable no site. **Nunca coloque a chave service_role no GitHub ou no navegador.**

## 2. Publicar no GitHub Pages

1. Abra **Settings → Pages** neste repositório.
2. Em **Build and deployment**, selecione **Deploy from a branch**.
3. Escolha a branch `main` e a pasta `/(root)`, depois salve.
4. Aguarde o GitHub informar a URL publicada. O endereço esperado é:
   `https://kerberimoveis.github.io/kerber-indicadores-comerciais/`

## 3. Como funciona

- Cada envio registra os números de uma equipe em uma data.
- A mesma equipe não pode ter dois lançamentos na mesma data.
- Os quatro gráficos comparam as equipes por dia no período selecionado.
- Os dados são diários, não acumulados no mês.

## Atenção: acesso sem login

O fluxo permite leitura e inserção pública, conforme a decisão de não exigir login. Qualquer pessoa que conheça o endereço pode tentar enviar dados. Duplicidades são bloqueadas e não há permissão pública de atualização ou exclusão. Até implementarmos um mecanismo administrativo protegido, correções devem ser feitas no painel do Supabase. Para uso interno mais seguro, recomendamos adicionar PIN por equipe ou validação anti-spam antes de divulgar o endereço.
