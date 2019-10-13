# CNN_project

## Introduction

Les réseaux de neurones multicouches sont au minimum constitués de :

- un couche d’entrée, qui capte l’information initiale et la transmet à la couche suivante.
- une couche de sortie, qui fournis une prédiction par exemple la classe à laquelle appartient une image dans le cadre d’un algorithme de classification multiclasse.
- une couche intermédiaire, aussi appelée couche cachée qui résalise des transformations intermédiaires.

### Fonctionnement d’un neurone 

Le modèle le plus simple est appelé perceptron. Il dispose d’une seule couche cachée.
Chaque neurone, qui transmet une information, est caractérisé par son poids et une fonction d’activation qui vont influencer l’activation, ou non, du neurone.
 
Schéma de Neurones de Somme pondérée

> Imaginons que vous hésitiez à partir en vacances. Vous réalisez une liste de pour (besoin de vous reposer, être en famille, sortir du quotidien …) et de contre (coûts des vacances, pas assez de congés …). Chaque argument aura un poids différent dans la décision finale que vous allez prendre. Il s’avère que votre situation financière ne vous permettent pas d’accomplir le voyage de vos rêves. Vous n’avez donc pas activez cette possibilité. Les réseaux neuronaux fonctionnent de la même manière!

Aussi, une fonction d’activation est nécessaire puisque l’information d’entrée n’est pas linéaire. Il faut donc appliquer une transformation non-linéaire à la somme pondérée.
Les deux fonctions d’activation les plus connues sont:
	- ReLu: f(x) = max(0;x)
	- Sigmoide:  f(x)=1/1+e-x

Le choix de la fonction d’activation est différent selon le problème posé (régression, classification)

L’apprentissage d’un réseau de neurone permet de déterminer le poids optimal de chacun des neurones. A chaque envois de sous-échantillons des données initiales à travers le réseau de neurones, une erreur de prédiction est calculée (généralement une erreur quadratique). Grace a l’algorithme de gradient, les poids sont mis a jours en calculant la dérivée de l’erreur par rapport à chaque wi. 


## Les réseaux convolution

Les réseaux convolutions ont connu un important développement ces dernières années, notamment pour le Deep Learning (reconnaissance d’image, l’analyse de texte..).

### Couche de convolution
Dans un premier temps, la matrice est passée a travers un filtre convolutif pour générer une opération de convolution.
Cette opération implique une perte d’information. En effet, le noyau du filtre ne peut pas se déplacer sur les bords de la matrice et entraine une diminution de la matrice de sortie (de taille M-n+1). Pour pallier à cela, il est courant d’appliquer un padding de 0, qui ajoute une bordure autour de l’image.
Cette étape réitérée permet, dans les premières convolutions, d’identifier des éléments de l’image simples tels que des traits, puis des contours et enfin des formes plus complexes.

### Activation
On applique ici une fonction d’activation à la sortie de la couche de convulation de la même manière que pour le perceptron.

### Pooling
Le pooling est une opération qui permet de réduire la dimension d’une matrice, où celle ci est subdivisées en plusieurs fenêtres desquelles on ne garde que le maximum ou la moyenne.
Le MaxPool est un filtre, généralement de taille 2*2, qui permet d’obtenir le maximum d’un sous-ensemble de la matrice. Il se déplace d’un saut de 2 pour éviter le chevauchement.

### DroPout
L’application d’un DropOut désactive aléatoirement certains neurones. Il permet d’éviter le sur-apprentissage en bloquant le passage de l’information.

## Architecture d’un réseau de neurones

Il n’existe pas d’architecture parfaite prédéfinie. Chaque projet aura une structure optimale différente qui sera trouvée en testant plusieurs combinaisons de couches.

{::options parse_block_html="true" /}

<div class="panel panel-info">
**Note**
{: .panel-heading}
<div class="panel-body">

NOTE DESCRIPTION

</div>
</div>
