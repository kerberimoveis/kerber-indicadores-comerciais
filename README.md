# Kerber Imóveis · Indicadores Comerciais

Painel interno para registrar e acompanhar os resultados diários das equipes da Kerber Imóveis. O dashboard reúne os lançamentos em um único lugar e apresenta comparativos por equipe e por período.

<p align="center">
  <strong>CANOAS · POA · POA ZS · VIAMÃO</strong>
</p>

**Acesse o painel:** [kerberimoveis.github.io/kerber-indicadores-comerciais](https://kerberimoveis.github.io/kerber-indicadores-comerciais/)

---

## Visão geral

O sistema foi desenvolvido para facilitar o acompanhamento dos indicadores comerciais, com uma interface adaptada para computadores e celulares.

### Indicadores acompanhados

- **Pré-Cadastros**
- **Mesas Marcadas**
- **Fechamentos**
- **Assinaturas**

### Equipes

| Equipe | Identidade visual |
|---|---|
| CANOAS | Vermelho · Esparta |
| POA | Azul · Celta |
| POA ZS | Amarelo · Ultras |
| VIAMÃO | Verde · Persa |

## Funcionalidades

- Formulário para registrar os indicadores de uma equipe em uma data.
- Painel com o resultado do dia anterior, separado por equipe.
- Quatro gráficos comparativos, um para cada indicador.
- Filtro de período para consultar os resultados entre duas datas.
- Período inicial dos gráficos definido automaticamente para a semana atual: de segunda-feira até o dia de hoje. As datas são recalculadas ao abrir ou recarregar a página.
- Dias sem lançamento são exibidos como lacunas nos gráficos, sem criar resultados fictícios.
- Equipes sem lançamento aparecem identificadas como **“Sem lançamento”** no painel, mantendo zero nos cálculos.
- Tratamento de falhas de conexão, com até três tentativas nas consultas de leitura.

> **Importante:** os números são lançamentos diários, não valores acumulados. Cada equipe pode registrar apenas um lançamento por data.

## Como utilizar

1. Abra o [dashboard](https://kerberimoveis.github.io/kerber-indicadores-comerciais/).
2. No formulário **Lançamento diário**, selecione a equipe e a data.
3. Informe os valores de Pré-Cadastros, Mesas Marcadas, Fechamentos e Assinaturas.
4. Clique em **Salvar indicadores do dia**.
5. Consulte o painel do dia anterior e os gráficos comparativos.
6. Para analisar outro intervalo, altere os campos **De** e **Até** e clique em **Atualizar gráficos**.

### Correções de lançamentos

O sistema impede mais de um lançamento para a mesma equipe na mesma data. No momento, não há edição ou exclusão pública pelo dashboard. Se um lançamento precisar de correção, solicite ao administrador (Gustavo), que fará o ajuste diretamente no Supabase.

## Tecnologias

- **HTML, CSS e JavaScript:** estrutura, estilo e funcionalidades da interface.
- **Supabase:** banco de dados e API para armazenamento e consulta dos indicadores.
- **Chart.js:** geração dos gráficos comparativos.
- **GitHub Pages:** hospedagem do dashboard.

## Estrutura do projeto

```text
kerber-indicadores-comerciais/
├── index.html
├── README.md
├── supabase/
│   └── schema.sql
├── LOGO KERBER.jpeg
├── LOGO SPARTA.png
├── LOGO CELTA.png
├── LOGO ULTRAS.png
└── LOGO PERSA.png
```

- `index.html`: aplicação do dashboard.
- `supabase/schema.sql`: estrutura da tabela, validações e políticas de acesso do banco.
- Arquivos de imagem: identidade visual da Kerber Imóveis e das equipes.

## Configuração do Supabase

Estas instruções são destinadas à configuração ou recriação do ambiente.

1. Crie um projeto no [Supabase](https://supabase.com/).
2. No projeto, abra o **SQL Editor**.
3. Execute o conteúdo completo do arquivo `supabase/schema.sql`.
4. Em **Project Settings → API**, obtenha a **Project URL** e a chave pública **Publishable** (ou a chave legada **anon**).
5. No `index.html`, configure as constantes `SUPABASE_URL` e `SUPABASE_ANON_KEY` com esses valores.

Use somente a chave pública Publishable/anon no frontend. **Nunca coloque uma chave `service_role`, secret ou outra credencial privada no HTML, no navegador ou no repositório.**

### Estrutura dos dados

A tabela utilizada é `public.indicadores_diarios`, com os seguintes campos principais:

| Campo | Descrição |
|---|---|
| `data` | Data do lançamento |
| `equipe` | CANOAS, POA, POA ZS ou VIAMÃO |
| `pre_cadastros` | Quantidade de pré-cadastros |
| `mesas_marcadas` | Quantidade de mesas marcadas |
| `fechamentos` | Quantidade de fechamentos |
| `assinaturas` | Quantidade de assinaturas |
| `criado_em` | Data e hora de criação do registro |

O banco aplica validações para aceitar somente as quatro equipes cadastradas e valores inteiros não negativos. Também possui uma restrição única para a combinação de equipe e data.

## Publicação

O dashboard é hospedado pelo GitHub Pages neste endereço:

[https://kerberimoveis.github.io/kerber-indicadores-comerciais/](https://kerberimoveis.github.io/kerber-indicadores-comerciais/)

As alterações publicadas na branch principal `main` são disponibilizadas pelo processo de publicação configurado no repositório. Após um novo commit, aguarde a conclusão da publicação; se necessário, atualize o navegador com **Ctrl + F5**.

## Acesso e segurança

O dashboard foi configurado para uso interno sem exigir login. Por isso, as operações de leitura e envio de lançamentos estão disponíveis publicamente por meio da chave pública do Supabase.

As políticas atuais do banco permitem:

- Consultar os indicadores.
- Inserir novos lançamentos válidos.

As políticas atuais não permitem atualização ou exclusão públicas. A restrição de um lançamento por equipe e data é aplicada também no banco de dados.

**Atenção:** como não há autenticação de usuários, o endereço do painel não funciona como controle de identidade. Compartilhe o link somente com as pessoas que devem utilizar o sistema. Nunca exponha credenciais privadas do Supabase.

---

**Kerber Imóveis** · Painel interno de indicadores comerciais
