# Livro de Receitas

Um site minimalista para guardar receitas — perfeito para receitas de família, adaptações de receitas encontradas online ou criações próprias.

Funcionalidades:
* Receitas em formato [Markdown](https://daringfireball.net/projects/markdown), basta criar o arquivo e fazer o upload
* Lista de receitas gerada automaticamente com navegação alfabética
* Cada receita é exibida em um formato limpo, pensado para uso enquanto cozinha ou no mercado — sem anúncios ou distrações
* Links automáticos para busca de imagens no Google, receitas e restaurantes próximos
* Para marcar o passo atual enquanto cozinha, clique nele para destacá-lo; clique novamente para remover o destaque, ou use as setas do teclado para avançar
* Código simples e bem comentado, fácil de personalizar


## MAIS INFORMAÇÕES
* [Formato das receitas](#formato-das-receitas)
* [Adicionando imagens](#adicionando-imagens)
* [Outras opções](#outras-opções)
* [Créditos](#créditos)


## FORMATO DAS RECEITAS
O arquivo Markdown da receita deve ter o nome em letras minúsculas com hífens no lugar dos espaços (ex: `arroz-de-forno.md` ou `bolo-de-fuba.md`). Esse nome será usado para popular a lista de receitas na página principal.

Use o `recipe-template.md` como ponto de partida, ou siga este formato:

```markdown
# TÍTULO
Subtítulo opcional

## info
* Cerca de XXX minutos
* XXX porções

## ingredientes
*

## passos
1.

## notas
*

## fonte
* url de onde a receita veio
```

Exemplo:

```markdown
# Brigadeiro de Cacau

## info
* Cerca de 30 minutos
* 30 unidades

## ingredientes
* 1 lata de leite condensado
* 3 colheres de sopa de cacau em pó
* 1 colher de sopa de manteiga
* Granulado para enrolar

## passos
1. Misture o leite condensado, o cacau e a manteiga em uma panela
2. Cozinhe em fogo médio, mexendo sempre, até desgrudar do fundo
3. Deixe esfriar, enrole e passe no granulado

## notas
* Para um sabor mais intenso, use cacau 100%
```

As seções `info`, `notas` e `fonte` são opcionais.

A seção `ingredientes` e `passos` pode ser dividida com sub-rótulos de texto simples (sem usar `##`):

```markdown
## passos
1. Misture os ingredientes secos
2. Adicione a água aos poucos

Para fritar:
1. Aqueça o óleo em fogo médio
2. Frite até dourar
3. Escorra em papel toalha
```


## ADICIONANDO IMAGENS
Se houver uma imagem `.jpg` com o mesmo nome do arquivo da receita, ela será exibida automaticamente como imagem de destaque.

Por exemplo: `brigadeiro-de-cacau.md` deve ter uma imagem chamada `brigadeiro-de-cacau.jpg` na pasta `images`.

Também é possível incluir imagens dentro da receita usando a sintaxe Markdown: `![texto alternativo](url)`.


## OUTRAS OPÇÕES
O arquivo `recipe.html` contém algumas opções de personalização:

* `yelpLocation`: cidade/estado para buscas no Yelp. Sem necessidade de formatação especial: `São Paulo SP`
* `helpUrls`: lista de links de ajuda com `label` (texto exibido) e `url` em formato de template. A string `<name>` será substituída pelo nome da receita
* `lookForHeroImage`: ativado por padrão; desative se não quiser usar imagens de destaque
* `autoUrlSections`: lista de seções onde URLs simples são convertidas em links clicáveis. Ideal para a seção `fonte`
* `shortenUrls`: exibe apenas o domínio principal de URLs longas (o link continua funcionando normalmente). Desativado por padrão

**Atenção:** ao adicionar ou remover receitas, execute `./update-recipes.sh` para regenerar o arquivo `recipes.json`.


## CRÉDITOS
Este projeto é baseado no [Recipes](https://github.com/jeffThompson/Recipes) de [Jeff Thompson](http://www.jeffreythompson.org/). O código original foi adaptado e traduzido para português.
