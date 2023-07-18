# musees-analysis

Ressource : Modules et librairies
  
Modules et librairies
1. Introduction
Hier, nous avons vu que le langage Python peut servir pour des projets très divers (de la création d'applications à l'analyse de données). Nous allons découvrir aujourd'hui ce qui a fait le succès de Python dans la data : ses librairies spécialisées pour l'analyse de données. Mais comprenons d'abord ce que sont les modules et les librairies 📚📚

📌 Utilité pour le projet : 1/5
📊 Utilité pour être Data Analyst : 1/5
💡 Pourquoi cette ressource ? : Introduire le concept de librairies et comprendre comment ça fonctionne.

2. La ressource
Peut-être qu'hier, lors de ta première journée Python, tu as été bloqué par moments car tu ne trouvais pas de fonction native correspondant à ce que tu voulais faire. Par exemple, pour calculer la racine carrée d'un nombre. Ou alors, peut être que dans tes recherches, tu es tombé sur des programmes qui commençaient par plusieurs import à la suite. A la fin de la journée, ces situations n'auront plus de secret pour toi.

3.1. Les modules
3.1.1 Définition d'un module
On appelle module tout fichier constitué de code Python (c’est-à-dire tout fichier avec l’extension .py) importé dans un autre fichier ou en mode interactif (cad quand tu es sur ton Notebook). Les modules permettent la séparation et donc une meilleure organisation du code. Autre avantage : certains modules te font économiser du temps car ils contiennent déjà des fonctions que tu n'auras pas besoin de ré-écrire à ton tour.

En Python, on peut distinguer trois grandes catégories de module en les classant selon leur éditeur :

Les modules standards qui ne font pas partie du langage en soi mais sont intégrés automatiquement par Python ;
Les modules développés par des développeurs externes qu’on va pouvoir utiliser ;
Les modules qu’on va développer nous-mêmes.
3.1.2 Utiliser un module
Un programme Python va généralement être composé d’un script principal qui va importer différents modules (c’est-à-dire différents fichiers Python) pour pouvoir les utiliser.
Pour importer un module, on utilise la syntaxe import nom-de-mon-module.

Dans un second temps, pour utiliser les éléments du module dans notre script, il faudra préfixer le nom de ces éléments par le nom du module et un point. Cela permet d’éviter les conflits dans le cas où on aurait défini des éléments de même nom que ceux disponibles dans le module.

Par exemple, prenez votre éditeur favori et créez un fichier fibo.py dans le répertoire courant qui contient :

# Fibonacci numbers module

def fib(n):    # write Fibonacci series up to n
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a+b
    print()

def fib2(n):   # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)
        a, b = b, a+b
    return result
Maintenant, ouvrez un interpréteur et importez le module en tapant :

> import fibo

Vous pouvez maintenant appeler les fonctions via le nom du module que vous venez de créer :

> fibo.fib(1000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987
> fibo.fib2(100)
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
💡💡 ASTUCE 💡💡

Si vous ne souhaitez pas réécrire le nom du module à chaque fois, vous avez deux autres options :

soit donner un alias au nom de votre module, pour n’avoir à écrire que l’alias : import fibo as fb
soit importer des fonctions spécifiques que vous pourrez ensuite utiliser comme des fonctions/variables Python natives (sans la notation .) : from fibo import fib
Un cas particulier de cette dernière méthode est d’importer en une ligne tous les objets contenus dans un module via la notation *. Néanmoins, ce n’est pas la méthode préconisée, afin d’éviter par exemple les conflits entre plusieurs modules qui pourraient avoir un nom de fonction identique.
from fibo import *

3.1.3 Modules standards
Comme tu l'as lu au début de cette leçon, nous importons bien souvent des modules créés par d’autres développeurs ou des modules mis à notre disposition par Python lui-même.
En effet, il existe un grand nombre de modules préconçus et prêts à l’emploi qui sont fournis d’office avec Python. Ces modules vont étendre le langage et nous permettre de réaliser toutes sortes d’opérations, notamment grâce aux fonctions qu’ils nous fournissent. Pour importer un module Python, nous allons à nouveau tout simplement utiliser une instruction import comme si on importait l’un de nos modules.

Les modules Python standards à connaitre sont les suivants :

Le module cgi (“Common Gateway Interface” ou “Interface de Passerelle Commune” en français) fournit des éléments permettant à des programmes Python de s’exécuter sur des serveurs HTTP ;
Le module datetime fournit des classes pour manipuler de façon simple ou plus complexe les dates et les heures ;
Le module json permet l’encodage et le décodage de données au format JSON ;
Le module math fournit un ensemble de fonctions permettant de réaliser des calculs mathématiques complexes ;
Le module os fournit une manière portable d’utiliser les fonctionnalités dépendantes du système d’exploitation ;
Le module random implémente des générateurs de nombres pseudo-aléatoires pour différentes distributions.
Vous pouvez retrouver la liste complète des modules standards Python sur le site de la documentation.

3.2. Les librairies
3.2.1 Définition d'une librairie
Quand on a un grand nombre de modules, il peut être intéressant de les organiser dans des dossiers. Un dossier qui rassemble des modules est appelé un package (paquet ou librairie en français).

Une librairie est donc une collection, un ensemble de modules Python. Comme vous l’avez vu ci-dessus, un module est un fichier Python. Un package est simplement un dossier contenant plusieurs fichiers Python (.py) et un fichier additionnel nommé init.py. Ce dernier différencie un package d’un dossier lambda contenant uniquement des codes Python.

On va pouvoir importer des paquets de la même façon que des modules et accéder à un module ou à un élément en particulier en utilisant la syntaxe nom-paquet.nom-module.nom-element.

Par exemple, on crée un dossier package1 dans lequel on place le fichier module1.py suivant :

def fonction1(a):
    return a**2
On peut ensuite utiliser la fonction fonction1() définie dans module1.py, en important package1.module1 comme dans l’exemple qui suit :

import package1.module1

u = package1.module1.fonction1(3)
print("u vaut", u)
3.2.2 Les librairies dans l'analyse de données
Les packages sont omniprésents dans l’analyse de données avec Python. En effet, de nombreux packages ont été créés spécifiquement pour répondre aux problématiques du domaine. Au fur et à mesure de la formation data, tu vas être amené à :

manipuler des données pour en faciliter l’analyse ;
réaliser différents graphiques pertinents représentant le comportement de tes données ;
utiliser des méthodes statistiques ;
faire tourner des algorithmes de machine learning plus ou moins compliqués ; etc.
Et pour réaliser tout cela, il te sera indispensable de maîtriser les différents objets et fonctions issus des librairies correspondantes. Avec les autres ressources du jour, tu vas déjà découvrir deux librairies indispensables pour l'analyse de données. J'espère que tu es au taquet 💪💪

4. Points importants à retenir
Dans cette leçon, nous avons vu ensemble les bases de l’utilisation des modules et des packages :

un module est un fichier contenant du code Python qui peut définir des fonctions, des classes et/ou des variables ;
vous pouvez importer n’importe quel module Python via le mot clé import;
pour utiliser une fonction d’un module, ou une classe ou une variable, il faut utiliser l’opérateur .;
une librairie ou package est un ensemble de plusieurs modules Python ;
il existe de nombreux packages spécifiquement créés pour l’analyse de données.
5. Pour aller plus loin
Découvrir le module random avec le cours OC et faire le quizz qui suit 👣👣
Ressource : La librairie NumPy
  
La librairie NumPy
Tu t'inquiétais de n'avoir toujours pas croisé de tableaux ? Rassure-toi, les tableaux NumPy sont dans la place 🤘🤘

1. Introduction
NumPy est une bibliothèque Python destinée à manipuler des matrices ou tableaux multidimensionnels ainsi que des fonctions mathématiques opérant sur ces tableaux. Dit comme ça, ça fait un peu peur mais en gros, dis toi que tu utiliseras NumPy quand tu travailleras avec des tableaux.

📌 Utilité pour le projet : 1/5
📊 Utilité pour être Data Analyst : 4/5
💡 Pourquoi cette ressource ? : En fait, NumPy te sera très utile quand tu auras acquis de l'expérience (ou que tu feras de la data science) car de très gros tableaux (numpy arrays) sont plus efficaces que de très gros dataframes (pandas). Néanmois, la librairie est traditionnellement présentée en tout début de formation car tu dois l'importer si tu veux utiliser les opérateurs arithmétiques de base comme la moyenne, la racine carrée etc.

2. Historique et contexte
Comme on l'a déjà vu, le langage Python n'a pas été conçu à l'origine pour le calcul numérique. Cependant, il a très tôt attiré l'attention de la communauté scientifique et technique.

En 1995, le groupe d'intérêt spécial (SIG) Matrix-sig a été fondé dans le but de créer un paquet de calcul matriciel. Parmi ses membres, Guido van Rossum, concepteur et développeur de Python, a étendu sa syntaxe, et en particulier, la syntaxe d'indexation, afin de faciliter le calcul des tableaux. Une première implémentation d'un paquetage matriciel a été réalisée par Jim Fulton, puis améliorée par Jim Hugunin et appelée Numeric, également connue sous le nom de "Numerical Python extensions" ou "NumPy".

NumPy est la base de SciPy, regroupement de bibliothèques Python autour du calcul scientifique 💣💣

Pour info, au cas où tu es largué dans ces histoires de calcul : le calcul scientifique est une discipline aux contours pas toujours franchement définis, mais qui regroupe un ensemble de champs mathématiques et informatiques permettant la simulation numérique des phénomènes de la physique, chimie, biologie, et sciences appliquées en général.

3. La ressource
On va découvrir ici à quoi la librairie NumPy va te servir.

A chaque fois que tu en auras besoin, n'oublie pas de l'importer au début de ton script :

import numpy as np

3.1. Les tableaux multidimensionnels
Le principe fondamental de NumPy est l'apport de tableaux multidimensionnels.

Par définition, un tableau (ou array) en anglais est une structure de données constituée d’une collection d’éléments (du même type) identifiés par un index.

Un exemple de tableau

L’image ci-dessus nous donne un exemple d’un tableau à 1 dimension. Ainsi, on parlera de tableaux multidimensionnels lorsqu’on aura au minimum deux dimensions 🙃 On peut définir la dimension d’un tableau comme le nombre d’indices (d’axes) nécessaires pour spécifier de manière unique un élément dans le tableau.

Les dimensions

On voit ici des exemples de tableaux à une, deux et trois dimensions. C’est un peu plus compliqué de représenter les dimensions supérieures à 3.

Attention, il ne faut pas confondre les listes et les tableaux. Contrairement aux listes en Python, les tableaux Numpy ne peuvent contenir des membres que d'un seul type. Par ailleurs, la grande différence entre ces deux structures de données se trouve au niveau des fonctions que vous pouvez leur appliquer. Par exemple, vous pouvez diviser un tableau (valeurs numériques) par 5, et chaque nombre dans le tableau sera divisé par 5 et vous aurez le résultat voulu. Cependant, si vous essayez de diviser une liste (valeurs numériques) par 5, l’interpréteur Python vous retournera une erreur.

Enfin, dis toi que tu vas pouvoir analyser beaucoup de choses en tant que tableaux de nombres. Par exemple, une image peut être considérée comme un tableau de deux dimensions (une matrice) où chaque nombre représente l'intensité lumineuse d'un pixel.

3.2. Manipulations de tableaux
Regarde comment créer et manipuler des tableaux sur ce cours d'introduction à NumPy.

3.2. Intérêt des tableaux
Mais surtout le plus important est que tu comprennes l'intérêt de NumPy pour l'analyse de données.

Les éléments d'un tableau sont stockés dans des emplacements de mémoire contigus. En fait, l’idée de NumPy est de stocker plusieurs éléments du même type ensemble dans le but d’améliorer les performances de calcul.

Cela est très utile car les boucles peuvent êtres lentes en Python. Si vous voulez savoir pourquoi, l'idée principale est la suivante : l'implémentation de référence de Python, encore appelée CPython, est très flexible, mais cette flexibilité l'empêche d'utiliser toutes les optimisations possibles. Avec des boucles, il faudra plusieurs secondes pour accomplir un million d'opérations. Sachant que les processeurs actuels sont capables d'exécuter des milliards d'opérations par seconde, cette durée peut apparaître absurde. Ce délai est dû à toutes les opérations annexes que doit accomplir l'interprète, comme les appels de fonction et vérifications de type ⏳⏳⏳

🔧🔧 ASTUCE 🔧🔧

À chaque fois que tu te retrouves à utiliser une boucle pour effectuer une opération en Python, demande-toi si cette opération ne peut pas s'accomplir grâce à Numpy sans boucle.

4. Points importants à retenir
NumPy permet une manipulation aisée et flexible des tableaux.
NumPy est important dans l'analyse de donnée pour sa redoutable efficacité. L’idée principale derrière les tableaux est de stocker plusieurs éléments du même type ensemble dans le but d’améliorer les performances de calcul.
5. Pour aller plus loin
La documentation officielle.

Ressource : La librairie Pandas
  
La librairie Pandas
Peut-être la ressource qui te servira le plus dans ton quotidien de Data Analyst. Donc ouvre grand les oreilles bébé panda 🐼🐼🐼🐼🐼

1. Introduction
Ici, tu verras l'intérêt de la librairie Pandas, ainsi que les opérations basiques sur l'objet phare de cette librairie, le dataframe.

📌 Utilité pour le projet : 5/5
📊 Utilité pour être Data Analyst : 5/5
💡 Pourquoi cette ressource ? : Maîtriser le format le plus utilisé en analyse de données : le dataframe.

2. Historique et contexte
Entre 2007 à 2010, Wes McKinney a commencé à construire ce qui allait devenir Pandas alors qu'il était chercheur dans la société américaine AQR Capital.

🗣🗣 PAUSE ANECDOTE 🗣🗣

Après python, les pandas maintenant ... Pourquoi tant d'animaux dans ce cours ?

Python ne fait pas référence à un serpent. Guido van Rossum était plutôt un fan de la série télévisée Monty Python's Flying Circus, ce pourquoi il a choisi le nom Python en 1991.

Quant à la librairie Pandas, son nom est dérivé du terme "données de panel", un terme d'économétrie pour les jeux de données qui comprennent des observations sur plusieurs périodes de temps pour les mêmes individus. Son nom est également un jeu de mots sur l'expression "analyse de données Python".

3. La ressource
Parmi les bibliothèques Python de calcul scientifique, Pandas est la plus utile pour les opérations de Data Analyse et de Data Science. Etudions ses principales fonctionnalités et son object phare : le dataframe.

3.1. Passez de Numpy à Pandas
Cf. cette page du cours OC

3.2. Manipulez les données contenues dans vos DataFrames
Cf. cette page du cours OC

3.3. Effectuez les opérations d'algèbre relationnelle sur les DataFrames
Cf. cette page du cours OC

4. Points importants à retenir
La librairie Pandas est très utilisée en data science car elle permet entre autres de :

simplifier les manipulations de données avec les dataframes (valeurs manquantes, colonnes, etc…)
permettre d’agréger et fusionner les données très facilement grâce aux fonctions groupby, agg et merge
simplifier le calcul de moyenne, médiane, variance ou encore somme
bénéficier d’une indexation sophistiquée et simple d’usage.
Au-delà de la simplification d’usages complexes, Pandas est également facile à prendre en main et permet de lire simplement des données sous différents formats : fichiers CSV et texte, Microsoft Excel, bases de données SQL ...
Tu l'as compris, Pandas est très appréciée pour la multitude d’options qu’elle offre mais aussi pour sa prise en main rapide quand on débute. Si tu n'as pas encore tout saisi aux concepts de merge de tables, on va revoir ça demain avec SQL donc tu pourras te remettre dans le bain 🛁🛁

5. Pour aller plus loin
Hier, tu as découvert Python. Aujourd'hui, NumPy et Pandas. C'est bon, tu peux donc commencer à te plonger dans des jeux de données comme un vrai Data Analyst 😳😳

Tu n'es pas sûr d'avoir tout compris ? Ou tu as tout compris mais tu ne sais pas comment mettre ensemble toutes ses connaissances ?

Pas d'inquiétude, ça va venir naturellement avec la pratique. Avant de te lancer dans le projet, je t'invite à regarder à quoi ressemble une analyse de données. Voici un exemple d'analyse réalisée sur LA Covid-19 (oui tu nous pardonneras mais c'est très très à la mode en ce moment, impossible d'y échapper 🙄). Prends en de la graine car maintenant, c'est à toi de réaliser les projets du jour 😮

Tu peux aussi jeter un oeil au Cookbook de la doc de Pandas si tu veux encore plus d'exemples.

Projets : Le tour de France des musées !
  
Le tour de France des musées !
Ca y est, tu es déjà armé pour être Data Analyst, niveau junior. Tu vas aujourd'hui analyser ton premier fichier csv 👀

1. Introduction
Tu viens d'être recruté en tant que stagiaire Data Analyst par le Ministère de la Culture. Le précédent stagiaire avait réussi à récolter le maximum d'informations sur les musées français.
Comme première mission, ton manager te demande d'analyser avec Python le fichier csv obtenu et d'essayer de trouver des informations intéressantes dans ce fichier.

En fait, la 17ème Nuit européenne des musées a eu lieu le samedi 3 juillet 🏛🏛🏛 Pour revenir sur cet événement annuel, la personne responsable de la communication a été sollicitée pour écrire un article -je cite- "qui balance des infos insolites sur les musées en France".
Mais elle ne sait pas vraiment quoi raconter ... Elle espère que ton analyse de données l'aidera à se lancer dans la rédaction de son article 🙄🙄

2. Le projet
2.1. Télécharger le fichier csv et l'ouvrir sur ton notebook
Le travail réalisé par le stagiaire précédent a été mis en ligne sur la plateforme Opendata du gouvernement : data.gouv.fr. Tu peux retrouver son travail ici et télécharger le fichier csv concernant les musées de France métropolitaine.

Si tu es curieux, n'hésite pas à aller regarder le script Python qui a été réalisé et pourquoi il a fait cela. Cela te permettra de t'imprégner de la mentalité open source et de voir le genre de scripts que tu sauras faire à la fin de la formation.

2.2. Répondre aux questions posées par ton manager
Ton manager t'a donné une liste de questions pour te rendre la tâche plus concrète. Il t'a demandé de répondre à ces questions dans un premier temps en laissant apparentes tes requêtes sur le Notebook.

Combien y-a-t-il de musées en France métropolitaine ?
Dans quelle(s) ville(s) y-a-t-il de plus de musées ?
Quel est le nombre moyen de musées par ville ?
Quel est le nombre médian de musées par ville ?
Comment sont répartis les musées par type (en pourcentage) ?
Combien y-a-t-il de musées dont le nom commence par "Château" ?
Pour combien de musées dispose-t-on de l'adresse du site web ?
Quel département français possède le plus de musées sur son territoire ?
Quel département français possède le moins de musées sur son territoire ?
Combien de musées ont "Napoléon" dans leur nom ?
2.3. Proposer deux axes d'analyse supplémentaires
Tu rends la réponse aux 10 questions mais ton manager n'est pas totalement satisfait. Il trouve que cela manque encore d'informations vraiment croustillantes pour le grand public.

Il te demande alors un nouveau travail : peux-tu proposer deux sources de données complémentaires qui pourraient enrichir le fichier ? Les développeurs se chargeront de récupérer les données quand tu auras identifiées les sources.

Par exemple, si tu trouves un site qui donne la fréquentation de tous les musées français, je pense que la responsable de la communication sera contente de pouvoir ajouter dans son article un top 5 des musées les plus fréquentés, ainsi qu'un flop 5 de ceux où personne ne va jamais 👹👹

Ajoute à la suite de ton fichier Jupyter une cellule au format Markdown qui détaille les deux sources de données existantes qu'il serait utile d'ajouter au fichier csv initial, sur quel site on peut les obtenir et ce qu'elles apporteraient dans l'analyse.

Cela permettra à ton manager d'évaluer tes capacités de prise d'initiative et de recherche sur le web.

3. Rendu attendu
Un beau fichier Jupyter qui alterne entre code et texte et contient les 3 étapes du projet 🍹🍹

PS : le projet du jour est volontairement court pour te donner confiance. Si tu as encore du temps devant toi, n'hésite pas à requêter davantage le fichier des musées. La proactivité est une compétence indispensable pour être un bon Data Analyst.
