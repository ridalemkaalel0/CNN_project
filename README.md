# CNN_project

## Introduction

Les réseaux de neurones multicouches sont au minimum constitués de :

- une couche d’entrée, qui capte l’information initiale et la transmet à la couche suivante.
- une couche de sortie, qui fournie une prédiction par exemple la classe à laquelle appartient une image dans le cadre d’un algorithme de classification multiclasse.
- une couche intermédiaire, aussi appelée couche cachée qui résalise des transformations intermédiaires.

### Fonctionnement d’un neurone 

Le modèle le plus simple est appelé perceptron. Il dispose d’une seule couche cachée.
Chaque neurone, qui transmet une information, est caractérisé par son poids qui influence l’activation, ou non, du neurone.


<p align="center">
   <img src="https://github.com/ridalemkaalel0/CNN_project/blob/master/images/pytorch-perceptron2.jpg" alt="Sublime's custom image"/>
  <i> Fig 1 - Schéma du fonctionnement d'un perceptron </i><br>
  <br>
</p>



>Imaginons que vous hésitiez à partir en vacances. Vous réalisez une liste de pour (besoin de vous reposer, être en famille, sortir du quotidien …) et de contre (coûts des vacances, pas assez de congés …). Chaque argument aura un poids différent dans la décision finale que vous allez prendre. Il s’avère que votre situation financière ne vous permettent pas d’accomplir le voyage de vos rêves. Vous n’avez donc pas activez cette possibilité. Les réseaux neuronaux fonctionnent de la même manière!

<br>

Aussi, une fonction d’activation est nécessaire puisque l’information d’entrée n’est pas linéaire. Il faut donc appliquer une transformation non-linéaire à la somme pondérée.
Le choix de la fonction d’activation est différent selon le problème posé (fig 2)

L’apprentissage d’un réseau de neurone permet de déterminer le poids optimal de chacun des neurones. A chaque envois de sous-échantillons des données initiales à travers le réseau de neurones, une erreur de prédiction est calculée (généralement une erreur quadratique). Grace a l’algorithme de gradient, les poids sont mis a jours en calculant la dérivée de l’erreur par rapport à chaque poids  ![equation](https://latex.codecogs.com/gif.latex?w_%7Bi%7D). 



| Problème                 | Activation de la sortie | Fonction d'erreur  |
| :-------------:            |:-------------:| :-----:|
| Régression               | Linéaire (ReLU) <br> ![equation](https://latex.codecogs.com/gif.latex?f%28x%29%20%3D%20max%280%3Bx%29)    | Erreur quadratique <br> ![equation](https://latex.codecogs.com/gif.latex?%5Csum_%7Bi%7D%28f%28x_%7Bi%7D%29-y%7Bi%7D%29%5E2) |
| Classement binaire       | Sigmoïde   <br> ![equation](https://latex.codecogs.com/gif.latex?f%28x%29%20%3D%201/1-e%5E%7Bx%7D)     | Entropie croisée  <br> ![equation](https://latex.codecogs.com/gif.latex?-%5Csum_%7Bi%7D%5Csum_%7Bk%3D1%7D%5E%7BK%7D%20y_%7Bik%7Dlog%28f_%7Bk%7D%28x_%7Bi%7D%29%29)|
| Classement multi-classes | Softmax  <br> ![equation](https://latex.codecogs.com/gif.latex?s_%7Bk%7D%28x%29%20%3D%20%5Cfrac%7Be%5E%7Bx_%7Bk%7D%7D%7D%7B%5Csum_%7Bl%3D1%7D%5E%7BK%7De%5E%7Bx_%7Bl%7D%7D%7D)     | Entropie croisée |

<p align="center">
  <i> Fig 2 - Tables de choix des fonctions d'activation et d'erreur </i><br>
  <br>
</p>


## Les réseaux convolution

Les réseaux convolutions ont connu un important développement ces dernières années, notamment pour le Deep Learning (reconnaissance d’image, l’analyse de texte..).

### Couche de convolution
Dans un premier temps, la matrice est passée à travers un filtre convolutif pour générer une opération de convolution.
Cette opération implique une perte d’information. En effet, le noyau du filtre ne peut pas se déplacer sur les bords de la matrice et entraine une diminution de la matrice de sortie (de taille M-n+1). Pour pallier à cela, il est courant d’appliquer un padding de 0, qui ajoute une bordure autour de l’image.
Cette étape réitérée permet, dans les premières convolutions, d’identifier des éléments de l’image simples tels que des traits, puis des contours et enfin des formes plus complexes.

### Activation
On applique ici une fonction d’activation à la sortie de la couche de convulation de la même manière que pour le perceptron.

### Pooling
Le pooling est une opération qui permet de réduire la dimension d’une matrice, où celle ci est subdivisées en plusieurs fenêtres desquelles on ne garde que le maximum ou la moyenne.
Le MaxPool est une fenêtre, généralement de taille 2x2, qui permet d’obtenir le maximum d’un sous-ensemble de la matrice. Il se déplace d’un saut de 2 pour éviter le chevauchement.


<p align="center">
   <img src="https://github.com/ridalemkaalel0/CNN_project/blob/master/images/maxpool.jpeg" alt="Sublime's custom image"/>
  <i> Fig 3 - Exemple de MaxPool </i><br>
  <br>
</p>



### DropOut
L’application d’un DropOut désactive aléatoirement certains neurones (fig 4, les neurones 1 et 3 sont désactivés). Il permet d’éviter le sur-apprentissage en bloquant le passage de l’information.
L'application d'un DropConnect permet d'annuler aléatoirement les poids de certains neurones (fig 4, certaines liaisons entre la couche d'entrée et la couche cachée sont désactivées).

<p align="center">
  <img src="https://github.com/ridalemkaalel0/CNN_project/blob/master/images/dropout.jpeg" alt="Sublime's custom image"/>
</p>

<p align="center">
  <i> Fig 3 - Exemple de DropOut et DropConnect </i><br>
  <br>
</p>

## Architecture d’un réseau de neurones

Il n’existe pas d’architecture parfaite prédéfinie. Chaque projet aura une structure optimale différente qui sera trouvée en testant plusieurs combinaisons de couches.




