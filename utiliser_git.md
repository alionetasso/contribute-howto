# Utiliser Git

Cette page décrit le flux de travail à suivre pour l'utilisation de Git en vue d'éditer le contenu de ce dépôt.

## Configuration de Git

Il est important que Git soit bien configuré afin que les commits soient identifiés clairement et proprement.
En voici un exemple, contenant entre autres choses des *alias*.

```
[user]
	name        = Sogal
	signingkey  = sogal@volted.net
	email       = sogal@volted.net
[commit]
    gpgSign     = True
[push]
	default     = simple
[alias]
	co          = checkout
	ci          = "commit -a -m"
	st          = status
	br          = "!git --no-pager branch"
	df          = diff
	pl          = pull
    pu          = push
[core]
[core "pager"]
	log         = less
	blame       = less
	branch      = cat
```

## Clé SSH

Une fois que l'admin a créé le compte sur le dépôt Git, il faut s'y connecter et ajouter sa clé SSH dans les paramètres du compte.
Si vous n'avez pas de clés SSH, il faut en créer une comme suit:

```
[ ! -d $HOME/.ssh ] && mkdir $HOME/.ssh
cd $HOME/.ssh
ssh-keygen -t rsa -b 4096 -f my_ssh_key.rsa
```

On vous demande une phrase de passe qui chiffre la clé qui va être créée et évite son utilisation fraduleuse en cas de compromission de la machine.

## Récupération des sources

### Pour la 1ère fois

```
git clone git@git@github.com:alionetasso/blog.git
```

### Pour mise à jour

```
git pull
```

### Ajouter un fichier

Pour faire en sorte que Git puisse suivre les modifications d'un nouveau fichier, il faut:

```
git add chemin/vers/nouveau_fichier
```

### Enregistrer les modifications

Maintenant que vous avez modifier/ajouter, il faut valider tout ça (`commit` en anglais) et ajouter un message expliquant brièvement la modification:

```
git commit -am "mise à jour des liens dans la page xxx"
```

## Pousser les modifications

Vous pouvez ensuite rendre publique votre contribution via :

```
git push
```

