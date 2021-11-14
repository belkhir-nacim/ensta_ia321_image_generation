# IMPLEMENTATIONS


## GAN

### DCGAN

**Sources** : 
- https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html#introduction 
- Papier : Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks

**Dataset** : photos de célébrités (Celeb-A Faces dataset)

**Générateur** :
- (0): ConvTranspose2d(100, 512, kernel_size=(4, 4), stride=(1, 1), bias=False)
- (1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (2): ReLU(inplace=True)

- (3): ConvTranspose2d(512, 256, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (4): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (5): ReLU(inplace=True)

- (6): ConvTranspose2d(256, 128, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (7): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (8): ReLU(inplace=True)

- (9): ConvTranspose2d(128, 64, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (10): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (11): ReLU(inplace=True)

- (12): ConvTranspose2d(64, 3, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (13): Tanh()

La première couche consiste en le reshape du vecteur z ((100,1) -> (1,1,100)). Puis, on applique une convolution transposée avec aucun padding, ni stride (=1) et un kernel de taille 4.

Ensuite, pour transformer un input de dimensions (4,4,1024) en un output de dimensions (64,64,3) :
- on diminue la taille du channel (divise par 2 à chaque couche) en diminue le nombre de filtres appliqués par couche (divise par 2)
- on augmente la taille des autres dimensions (multiplie par 2 à chaque couche) en utilisant des convolutions transposée

**Discriminateur** :
- (0): Conv2d(3, 64, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (1): LeakyReLU(negative_slope=0.2, inplace=True)

- (2): Conv2d(64, 128, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (3): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (4): LeakyReLU(negative_slope=0.2, inplace=True)

- (5): Conv2d(128, 256, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (6): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (7): LeakyReLU(negative_slope=0.2, inplace=True)

- (8): Conv2d(256, 512, kernel_size=(4, 4), stride=(2, 2), padding=(1, 1), bias=False)
- (9): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- (10): LeakyReLU(negative_slope=0.2, inplace=True)

- (11): Conv2d(512, 1, kernel_size=(4, 4), stride=(1, 1), bias=False)
- (12): Sigmoid()

D’après le papier du DCGAN, c'est une bonne pratique d'utiliser la strided convolution plutôt que le pooling pour le subsampling car cela permet au réseau d'apprendre sa propre fonction de pooling. De plus, les fonctions de batch norm et de leaky ReLU favorisent une descente de gradient efficace, ce qui est essentiel pour le processus d'apprentissage de G et D.

**Problèmes** : 
- très long de dézipper le dataset complet -> (1) ou (2)
- (1) :  arrêter de dézipper avant la fin et travailler sur training set réduit MAIS training sur 5 epochs du training set réduit très long (1h)
- (2) : erreur lorsqu’on charge les données sur Google Colab à partir d’un fichier local -> il faut dézipper directement dans Google Drive à partir de Google Colab (commande !unzip), puis importer le dataset à partir de Google Colab

**Résultats** :
- Sur un training set réduit (15 000 images) : mauvaise qualité (images très floues et on devine des visages) et peu de diversité.
- Sur le training set complet (plus de 100 000 images) : qualité moyenne (visages déformés) et diversité correcte (obtenus sur le site du tutoriel).
