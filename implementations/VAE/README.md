# Implémentations des VAE

Voici une brève présentation des codes contenus dans ce dossier :

## VAE

Fichier : _vae.ipynb_

Modèle : VAE

Dataset : CIFAR10

Frameworks : pytorch, pytorch lightning

Papier scientifique : _Auto-Encoding Variational Bayes_, Diederik P. Kingma, Max Welling (2014) [Lien vers le papier](https://arxiv.org/abs/1312.6114)

Ce code est fonctionnel et permet d'entrainer un VAE et de générer de nouvelles images à partir des images données en entrée. Les outputs du notebook correspondent à un entrainement de 10 epochs (durée : 16 minutes). Vous pouvez retrouver les images générées lors d'un entrainement de 30 epochs (durée : 2h40) dans le rapport.

Il est possible que certaines erreurs de compatibilité entre les frameworks _pytorch-lightning_ et _pytorch-lightning-bolts_ apparaissent selon l'environnement que vous utilisez.

## VQ-VAE

Fichier : _vqvae.ipynb_

Modèle : VQ-VAE

Générateur : Transformer GPT2

Dataset : CIFAR10

Frameworks : TensforFlow 2 et Sonnet

Papier scientifique : _Vector Quantised-Variational AutoEncoder_, Van Den Oord et al. (2017). [Lien vers le papier](https://arxiv.org/abs/1711.00937)

Le code permet de réaliser l'apprentissage du modèle principal du VQ-VAE (encodeur, décodeur et codebook). Le résultat de cet apprentissage peut être évalué à l'aide
de courbes de perte (loss) et est visible sur les images reconstuites.

Cependant, lors de l'entrainement du générateur (transformer GPT2), nous obtenons une erreur provenant du GPU (cuda). Après de nombreuses tentatives (comme expliqué dans la partie "Difficultés et alternatives" du rapport), nous ne sommes pas arrivés à résoudre cette erreur. Il est donc impossible d'entrainer le générateur. Il n'est donc également pas possible de générer de nouvelles images à partir du dataset d'entrée.

## VQ-VAE-2

Fichier : _vqvae2.ipynb_

Modèle : VQ-VAE-2

Générateur : PixelCNN et Transformer GPT2

Datasets : CIFAR10 et Stanford Dogs

Frameworks : pytorch

Papier scientifique : _Generating Diverse High-Fidelity Images with VQ-VAE-2_, Ali Razavi et al. (2019). [Lien vers le papier](https://arxiv.org/abs/1906.00446)

Tout comme le code du VQ-VAE, il est possible d'entraîner le modèle (encodeur, décodeur et codebooks). On peut donc reconstruire les images des datasets.

A la différence du code du VQ-VAE, on peut également entrainer un générateur au choix entre un PixelCNN et le transformer GPT2.

Cependant, nous obtenons la même erreur provenant de cuda, lorsque nous donnons les indices des codes générés au décodeur pour qu'il puisse générer de nouvelles images. Cette toute dernière étape n'est donc pas réalisable avec ce code, malgré les alternatives que nous avos mis en oeuvre (voir la partie "Difficultés et alternatives" du rapport).