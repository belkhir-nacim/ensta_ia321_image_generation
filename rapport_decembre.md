# RAPPORT DE DÉCEMBRE
**Projet** : Génération d’images (Groupe 6)

**Date** : 01/12/21

**Tuteur projet** : Nacim Belkhir (nacim.belkhir@safrangroup.com)

**Membres du projet** : Lisa Giordani, Mouïn Ben Ammar, Yoldoz Tabei, Ilias Harkati



## Présentation du projet

Le deep learning est de plus en plus utilisé en entreprise, mais nécessite une très grande quantité de données. La génération d’images peut donc s’avérer une solution pour des problématiques de data augmentation ou encore de généralisation des modèles. C’est dans ce contexte que ce projet s’inscrit. Il portera sur la génération d’images en s’appuyant sur les deux stratégies principales existantes :  
les GAN (generative adversarial networks - réseaux antagonistes génératifs en Français) qui sont constitués d’un générateur et d’un discriminateur qui tente de deviner si une image est réelle ou a été créée par le générateur
les VAE (variational autoencoders - autoencodeur variationnels en Français) qui sont des estimateurs de distribution non paramétriques

Une application de ce travail pourrait être la data augmentation pour servir des modèles de détection d’anomalies sur des chaînes de production de pièces aéronautiques (chez Safran) par exemple ou encore l’apprentissage de représentations.

De nombreux algorithmes ont été développés par des chercheurs et ingénieurs du domaine et sont disponibles en ligne et/ou dans des papiers scientifiques. 
Au cours de ce projet, nous devrons ré-implémenter et tester certains des algorithmes existants que nous considérons comme pertinents au vu des ressources (GPU) et des compétences dont nous disposons. Pour ce faire, nous pourrons utiliser Google Collab, un petit cluster de calcul de l’ENSTA et un autre de Safran. Nous suivrons un cours pour apprendre à écrire des scripts permettant de lancer un code à distance sur les clusters. Nous écrirons des scripts, packagerons le code et nous serons vigilants au fait que le training puisse redémarrer seul à partir d’un checkpoint dans le cas où il s'arrêterait. M. Belkhir pourra alors récupérer le code que nous auront poussé sur GitHub et le lancer sur un cluster de Safran.
Afin de pouvoir juger des performances des algorithmes implémentés, nous devrons aussi déterminer des indicateurs permettant de discriminer les algorithmes. Ces indicateurs pourront se baser sur la cohérence et la variété des images générées.


## Objectifs du projet

Le projet se découpe en trois grandes parties :
1. Recherche et formation : constitution d’une bibliographie
2. Implémentation d’algorithmes
3. Présentation de nos recherches et de résultats via un blog et une soutenance

Les objectifs du projet sont les suivants :
- Réaliser un état de l’art sur le domaine des modèles génératifs d’images
- Ré-implémenter au moins un algorithme existant par nous-même
- Implémenter un algorithme de mesure de la qualité des images générées
- Tester l’algorithme de génération d’images implémenté sur une base de données (exemple : segmentation d’images de routes comme Cityscape si cela est possible, MNIST, SVHN, CIFAR)
- Mesurer ses performances en termes de cohérence et de diversité des images générées

Les rendus attendus sont :
- Fichiers de code
- Images générées
- Blog
- Soutenance oral avec une présentation PowerPoint


## Recherches bibliographiques

- https://www.inria.fr/fr/xgan-action-exploratoire-videos-gan-ia
- https://github.com/nashory/gans-awesome-applications
- https://towardsdatascience.com/what-is-transposed-convolutional-layer-40e5e6e31c11
- Goodfellow -  Generative Adversarial Nets (2014) : invention des GANs
- Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks (DCGAN)

doit montrer l’évolution des découvertes dans la recherche
choix de l’algo (difficile) à implémenter

Voir les sections [Bibliographie](ensta_ia321_image_generation/bibliographie/) et [Blog](ensta_ia321_image_generation/blog/) du GitHub.

## Premières implémentations

GAN :
- DCGAN

Voir la section [Implementations](ensta_ia321_image_generation/implementations/) du GitHub.
