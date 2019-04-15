# leny/vim-wrkshp

> 💡 A small, introductive workshop about vim, for [BeCode](//becode.org) juniors.

* * *

## Sommaire

1. Un (tout petit) peu d'histoire
	1. [`ed`](https://fr.wikipedia.org/wiki/Ed_(logiciel)) (1973, [Ken Thompson](https://fr.wikipedia.org/wiki/Ken_Thompson))
	1. [`ex`](https://fr.wikipedia.org/wiki/Ex_(%C3%A9diteur_de_texte)) (1976, Ken Thompson & Charles Haley)
	1. [`vi`](https://fr.wikipedia.org/wiki/Vi) (1976, [Bill Joy](https://fr.wikipedia.org/wiki/Bill_Joy))
	1. [`vim`](https://fr.wikipedia.org/wiki/Vim) (1991, [Bram Moolenaar](https://fr.wikipedia.org/wiki/Bram_Moolenaar))
	1. [`neovim`](https://fr.wikipedia.org/wiki/Neovim) (2014, communautaire)
	1. Les alternatives ([`nano`](https://fr.wikipedia.org/wiki/GNU_nano), [`emacs`](https://fr.wikipedia.org/wiki/Emacs))
	1. [La *grande* guerre des éditeurs](https://fr.wikipedia.org/wiki/Guerre_d%27%C3%A9diteurs)
1. Quid du _vim-mode_ ?
1. Installer `vim`
	1. Installation classique
		1. [`vim`](https://github.com/vim/vim#installation)
		1. [`neovim`](https://github.com/neovim/neovim/wiki/Installing-Neovim)
	1. Utilisation du docker **leny/vim**
1. Les bases
	1. Quitter `vim`
	1. Le _vimtutor_
	1. Un petit mot sur les *modes*
		1. `Normal`
		1. `Insert`
		1. `Visual`
		1. `Command`
	1. Les mouvements
		1. _Home Row_
		1. Autres mouvements
		1. Multiplicateurs
	1. Modifications
		1. Une incursion en `Insert` mode
		1. Opérateurs de modifications (`delete`, `change`, `replace`, `substitute`)
	1. Yank! Yank!
		1. Le copier/coller dans vim
		1. Les registres
1. Organisation de l'espace de travail
	1. Tabs
	1. Splits
	1. Buffers
1. Un peu plus loin…
	1. Mode `visual`
	1. Marks
	1. Macros
	1. Mode `command`
		1. Commandes vim
		1. Commandes "*natives*"
1. Configuration
	1. Un plongée en `.vimrc`
	1. Plugins & *dotfiles*
1. Et maintenant ?
	1. [Vim golf](https://www.vimgolf.com)
	1. **tmux**
		
## Ressources

[![XKCD: Real Programmers](https://imgs.xkcd.com/comics/real_programmers.png)](https://xkcd.com/378/)

### Liens utiles

* [vim-galore](https://github.com/mhinz/vim-galore) : une immense liste de ressources, tips, astuces, plugins…
* [Moving to neovim from vim](https://jacky.wtf/weblog/moving-to-neovim/) : une chouette étude de cas
* [Vim Zero](https://www.oliversherouse.com/2017/08/21/vim_zero.html) : un pas-à-pas autour d'une configuration avancée de vim, en partant de zéro
* [tmux and vim - even better together](https://blog.bugsnag.com/tmux-and-vim/) : le titre est assez explicite
* [This is my favorite vim cheat sheet…](https://www.reddit.com/r/vim/comments/32r85c/this_is_my_favorite_vim_cheat_sheet_does_anyone/) : un thread reddit autour d'une des plus chouettes *cheatsheet* sur vim
* [Survive Vim With these 5 Simple Tricks](http://blog.theodo.fr/2017/02/survive-vim-with-these-5-simple-tricks/)
* [Habit breaking, habit making](http://vimcasts.org/blog/2013/02/habit-breaking-habit-making/) : à propos du vim *hardmode*, un truc de _vrais_ barbus 😅
* [How to boost your Vim productivity](https://sheerun.net/2014/03/21/how-to-boost-your-vim-productivity/)
* [Why I use vim](https://pascalprecht.github.io/posts/why-i-use-vim/) : un bon article de fond avec pas mal de liens vers d'autres ressources
* [Vim speed is not really the point](https://wrongsideofmemphis.com/2013/03/27/vim-speed-is-not-really-the-point/) : un autre (vieil) article de fond, autour de la *raison d'être* de vim
* [10 essential Vim plugins for 2018](https://medium.com/@huntie/10-essential-vim-plugins-for-2018-39957190b7a9) : une chouette (et récente) liste de plugins pour vim

* * *

### Container docker

Je vous ai préparé un [container docker](https://hub.docker.com/r/leny/vim) qui contient _uniquement_ vim. Il vous permet de tester vim et/ou ses réglages sans risquer de "casser" votre config locale, ou de tester ce formidable éditeur sans avoir à l'installer.

Ce container est configuré avec deux volumes : le premier permet de *monter* un dossier de votre système pour y travailler avec vim, le second sert à stocker la configuration de vim pour qu'elle _persiste_ entre les lancements du container.

Pour lancer le container, il vous suffit d'utiliser la commande suivante :

	docker run -it -v $(pwd):/src -v vimconfig:/root leny/vim
	
Pour [ceusses](https://fr.wiktionary.org/wiki/ceusses) d'entre vous qui utilisent `fish`, la commande varie un tout petit peu : 

	docker run -it -v (pwd):/src -v vimconfig:/root leny/vim

#### vimtutor

Le container contient également _vimtutor_, que vous pouvez exécuter en le rajoutant à la commande pour lancer le container :

	docker run -it -v $(pwd):/src -v vimconfig:/root leny/vim vimtutor
