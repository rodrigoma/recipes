# RECIPE BOOK

A super minimal recipe website – great for keeping track of family recipes, mods to ones you find online, or have created yourself!

**See it in action here: [jeffreythompson.org/recipes](http://jeffreythompson.org/recipes)**

Features:
* Recipes in a simple [Markdown format](https://daringfireball.net/projects/markdown), just dump them in a folder and upload  
* List of recipes will auto-populate with quick alpha links at the top  
* Each recipe is displayed in a nice, clean format designed for use while cooking or at the grocery store – no extra 💩 or ads  
* Auto-generated links to a Google image search for that dish, recipes on Serious Eats and Google, and for restaurants on Yelp (in case you burn something and need takeout fast)  
* To save your place while scrolling up around on the page, click the step you're on to highlight it; click it again to remove the highlight, or use the left/right arrow keys to advance  
* Easily customized and code is (mostly) really well annotated 🙃  


## MORE INFO  
* [Recipe format](#recipe-format)
* [Adding images](#adding-images)
* [Other options](#other-options)
* [Suggestions welcome!](#suggestions-welcome)


## RECIPE FORMAT  
In order to show up properly, your recipe's Markdown file should be named with dashes in place of spaces (ex: `rice-pilaf.md` or `saag-paneer.md`). This will be used to populate your list of recipes on the main page.

Use `recipe-template.md` and/or follow this format:

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

For example:

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

You can optionally include info about how long the recipe takes and how many servings it makes. Put this before the `Ingredients` list:  

```## info
* Cerca de 90 minutos
* Suficiente para um curry grande
```

A seção `ingredientes` e `passos` pode ser dividida com sub-rótulos de texto simples (sem usar `##`):

```## passos
1. Misture os ingredientes secos
2. Adicione a água aos poucos

Para fritar:
1. Aqueça o óleo em fogo médio
2. Frite até dourar
3. Escorra em papel toalha
```

## ADDING IMAGES  
Thanks to a suggestion from @mpember, if you have a `jpg` image with the same filename as your recipe, it will automatically be added! 

For example: `aloo-matar.md` should have an image called `aloo-matar.jpg` in the `images` folder.

You can also include other images in the recipe using Markdown's image syntax: `![alt text](url)`. You'll probably want to update the stylesheet to size them appropriately.


## OTHER OPTIONS  
The `recipe.html` file also includes some more options you can customize:

* `yelpLocation`: the city/state where you're located to make Yelp searches easier! No need for fancy formatting, this will work fine: `Minneapolis MN`  
* `helpUrls`: dictionary with the `label` (text displayed) and `url` in template form. The string `<name>` will be replaced with your recipe's name  
* `lookForHeroImage`: on by default, but you can turn it off if you never intend to include hero images  
* `autoUrlSections`: lista de seções onde URLs simples (ex: www.instagram.com) são convertidas em links clicáveis. Ótimo para a seção `fonte`, mas não ideal se quiser usar links formatados em Markdown em outras seções
* `shortenUrls`: turns a super-long url into just the main domain name (link will still work as normal, just less cluttered). Off by default but exists if you want it

**Note:** When you add or remove recipe files, run `./update-recipes.sh` to regenerate the `recipes.json` file that contains the list of all recipes.


## SUGGESTIONS WELCOME  
If you have suggestions for improving this project, please let me know! Either [open an issue](https://github.com/jeffThompson/Recipes/issues/new) or send me an email.

