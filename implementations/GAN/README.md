# Implémentation des GAN

# DCGAN

Modèle : DCGAN

Dataset : Celeba

Framework : Pytorch

Papier scientifique : _Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks_, Alec Radford, Luke Metz, Soumith Chintala (2015). [Lien vers le papier](https://arxiv.org/abs/1511.06434)

![alt text](DCGAN_architecture.png)

**Générateur** :
La première couche consiste en le reshape du vecteur z ((100,1) -> (1,1,100)). Puis, on applique une convolution transposée avec aucun padding, ni stride (=1) et un kernel de taille 4.

Ensuite, pour transformer un input de dimensions (4,4,1024) en un output de dimensions (64,64,3) :
- on diminue la taille du channel (divise par 2 à chaque couche) en diminue le nombre de filtres appliqués par couche (divise par 2)
- on augmente la taille des autres dimensions (multiplie par 2 à chaque couche) en utilisant des convolutions transposée

**Discriminateur** :
D’après le papier du DCGAN, c'est une bonne pratique d'utiliser la strided convolution plutôt que le pooling pour le subsampling car cela permet au réseau d'apprendre sa propre fonction de pooling. De plus, les fonctions de batch norm et de leaky ReLU favorisent une descente de gradient efficace, ce qui est essentiel pour le processus d'apprentissage de G et D.

**Problèmes** : 
- très long de dézipper le dataset complet -> (1) ou (2)
- (1) :  arrêter de dézipper avant la fin et travailler sur training set réduit MAIS training sur 5 epochs du training set réduit très long (1h)
- (2) : erreur lorsqu’on charge les données sur Google Colab à partir d’un fichier local -> il faut dézipper directement dans Google Drive à partir de Google Colab (commande !unzip), puis importer le dataset à partir de Google Colab

**Résultats** :
- Sur un training set réduit (15 000 images) : mauvaise qualité (images très floues et on devine des visages) et peu de diversité.
- Sur le training set complet (plus de 100 000 images) : qualité moyenne (visages déformés) et diversité correcte (obtenus sur le site du tutoriel).


# StyleGAN
