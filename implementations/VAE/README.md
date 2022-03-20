# Implémentations des VAE

Voici une brève présentation des codes contenus dans ce dossier :

## VAE

Fichier : _vae.ipynb_

Modèle : VAE

Dataset : CIFAR10

Frameworks : 

Ce code est fonctionnel et permet d'entrainer un VAE et de générer de nouvelles images à partir des images données en entrée.
Néanmoins, il est possible que certaines erreurs de compatibilité entre les frameworks _pytorch-lightning_ et _pytorch-lightning-pblots_ apparaissent selon l'environnement que vous utilisez.

## VQ-VAE

Fichier : _vqvae.ipynb_

Modèle : VQ-VAE

Générateur : Transformer GPT2

Dataset : CIFAR10

Frameworks : TensforFlow 2 et Sonnet 

Le code permet de réaliser l'apprentissage du modèle principal du VQ-VAE (encodeur, décodeur et codebook). Le résultat de cet apprentissage peut être évalué à l'aide
de courbes de perte (loss) et est visible sur les images reconstuites.

Cependant,

## VQ-VAE-2

Fichier : _vqvae2.ipynb_

Modèle : VQ-VAE-2

Générateur : PixelCNN et Transformer GPT2

Datasets : CIFAR10 et Stanford Dogs

Frameworks :




