# Structure d'un module Odoo

**Note :** Je développe sur la version 12 de Odoo, il se peut que votre version présente quelques différences. 

**Objectif :** Créer un premier module, disponible dans la librairie d'applications.

Bonjour à toutes et à tous,
pour le premier article du blog, je vais vous apprendre à créer votre premier module basique pour Odoo. Nous ne mettrons aucun traitement ni aucune vue dans celui-ci, l’objectif est de vous montrer comment faire reconnaître à Odoo votre nouveau module. 

Pour commencer, je vais partir du principe que vous avez tous une version de Odoo fonctionnelle et que vous avez configuré votre environnement de développement pour correspondre à vos besoins. Personnellement j’utilise PyCharm mais vous êtes libre d’en choisir un autre. 

Si vous avez besoin d’aide pour télécharger et installer Odoo, je vous renvoie vers la documentation officielle qui est plutôt bien faite sur le sujet. 

Comme vous le voyez, j’ai donc un projet Odoo qui contient uniquement les sources officiels, et on ne va rien toucher dans ce répertoire si ce n’est le fichier de configuration. 

On va donc commencer par créer un répertoire, en dehors de celui d’Odoo pour placer tous nos modules supplémentaires. Personnellement j’ai fais le choix de faire une structure comme cela :
un répertoire Odoo qui contient les sources officielles
un répertoire oca-addons qui contient tous les modules qui sont issus de la communauté OCA
un répertoire custom-addons qui contient tous mes modules.

On commence donc par créer un nouveau projet en le placant quelque part sur notre disque en dehors du répertoire Odoo, et on choisi de l’attacher au panneau de visualisation des projets. Ca nous permet de tout garder sous la main pour développer plus facilement. 

On a donc désormais un répertoire vide, qui pourra contenir chacun de nos projets. 

La première étape que je vous propose de faire, c’est de modifier le fichier de configuration d’Odoo afin de lui préciser que nous avons besoin qu’il aille chercher nos modules quelque part sur le disque. Pour ce faire, on déplie le répertoire du projet Odoo, et on cherche notre fichier de configuration à la racine. La ligne qui nous intéresse est la ligne avec la clé “addons_path” et on va rajouter au bout de celle-ci, le chemin vers notre répertoire d’addons que l’on a créé précédement. Ensuite on peut replier le répertoire du projet, nous n’en aurons plus besoin. 

La seconde étape, c’est de créer un répertoire à l’intérieur du répertoire des addons que l’on a créé, pour y placer notre module. Pour la série de tutoriels, je vous propose de partir sur le développement d’une gestion de tickets pour un support technique. On va donc créer un répertoire “helpdesk” par exemple, qui correspondra au nom de notre module dans Odoo et on va pouvoir commencer à structurer celui-ci en commençant par les deux premier fichiers indispensables d’un module :
le fichier __init__.py 
le fichier __manifest__.py

Dans le fichier init, on va retrouver les imports  des fichiers python de notre module. Cette partie sera vue dans un tutoriel suivant donc pour l’instant on va juste créer un fichier vide. 

Le fichier manifest lui contient toutes les informations relatives à notre module, à savoir son nom, une description, des informations sur la version, les dépendances utilisées et les vues que l’on souhaite utiliser. 

C’est basiquement un fichier json avec plusieurs clés, certaines sont obligatoires et d’autres pas forcément indispensables, mais pour les besoins du tutoriel on va se contenter des plus importantes à savoir : 
un nom
une description
les dépendances 
et on va lui dire que c’est une application.

Structure du fichier __manifest__.py
```
{
    'name': "Module d'assistance",
    'description': """
        Notre module de support technique
    """,

    'author': "Thomas Brouwer",
    'version': '0.1',

    'depends': ['base'],

    'data': [
    ],
    'application': True
}
```

Plus tard nous verrons l’importation de vues qui seront obligatoires, mais je vous laisser consulter la liste en allant sur [la documentation officielle](https://www.odoo.com/documentation/12.0/reference/module.html). 

Une fois ce fichier créé, notre module est opérationnel et prêt à être reconnu par Odoo. 
On va donc lancer notre instance, puis une fois connecté on va se mettre en mode développeur en allant dans les paramètres, puis en cliquant sur "activer le mode développeur" en bas à droite. 

![alt text](https://raw.githubusercontent.com/yakoso/blog/master/medias/Screenshot_2020-06-10%20Tableau%20de%20bord%20-%20Odoo(1).png "Tableau de bord Odoo")

On doit désormais aller dans Applications, puis mettre à jour la liste des applications pour qu’Odoo scan les répertoires qui ont été mis dans le fichier de configuration. Une fois la liste à jour, on voit que notre module est disponible, et on peut l’installer en cliquant sur “Installer”. 

Voila, c’est toute pour ce premier tutoriel consacré à la création d’un premier module de base, dans le prochain, nous ferons un petit cahier des charges pour notre solution de support technique et on commencera à développer pour que tout ça prenne forme !
