# Markdown

À toute fin utile, voici un rappel de la syntaxe Markdown utilisée pour l'édition de l'ensemble des pages de ce wiki :

## Titre de page

```
Titre de ma page
================
```

## Niveau de titres

```
# Grand titre
## Titre secondaire
### Petit titre
```

## URL

```
[Texte de l'adresse](http://mon.url.tld)
ou en interne
[Texte de l'adresse interne](docs/page.md)
```

## Mise en forme du texte

```
*italique*
**gras**
```

## Code

    ```
    code
    ```
ou

`code en ligne`

## Image

```
![Texte de l'image aka. alt](chemin/vers/image)
```

Plus d'exemple sur la [page de syntaxe Markdown](https://daringfireball.net/projects/markdown/syntax).

## Table

```
Colonne 0 | Titre col.1 | Autre col.3
----------|-------------|-------------
Contenu   | Très long contenu dans cette colonne | Dernière colonne
Encore | une | ligne
Et puis | | la dernière ligne
```

Colonne 0 | Titre col.1 | Autre col.3
----------|-------------|-------------
Contenu   | Très long contenu dans cette colonne | Dernière colonne
Encore | une | ligne
Et puis | | la dernière ligne

## Convertir le Markdown

Installer le paquet `pandoc`:

```
zypper in pandoc
```

Lancer la conversion vers du *html* :

```
pandoc -f markdown+hard_line_breaks -t html -s -o md-preview.html fichier.md
```

## Astuces Markdown pour Vim

Parce qu'éditer du Markdown avec Vim, c'est l'assurance d'une place au paradis du grand [Monstre en spaghetti volant](https://fr.wikipedia.org/wiki/Pastafarisme), voici quelques astuces pour faciliter la vie :

### Raccourcis pour le gras et l'italique

```
" format markdown files
" F2 pour mettre la ligne en gras
autocmd FileType markdown nnoremap <F2> <Esc> I**<Esc>A**<Esc>
" F3 pour mettre la ligne en italique
autocmd FileType markdown nnoremap <F3> <Esc> I*<Esc>A*<Esc>
```

### Gérer le *filetype*, générer un aperçu dans Firefox (via conversion avec Pandoc)

```
" markdown options
" Définir le type de fichier en fonction de l'extension
autocmd BufNewFile,BufReadPost *.md set filetype=markdown
let g:markdown_fenced_languages = ['html', 'python', 'bash=sh']
" Appuyer sur 2 puis sur m immédiatement créer la conversion en html et affiche le rendu
au BufNewFile,BufRead *.md map 2m :w<CR>:!pandoc -f markdown+hard_line_breaks -t html -s -o /tmp/vim-md-preview.html "%" ; firefox "file:///tmp/vim-md-preview.html" & <CR><CR>
```
