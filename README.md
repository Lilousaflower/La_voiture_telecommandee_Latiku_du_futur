# Robot Télécommandé - *Lakitu du Futur* 
Documentation pour vous permettre de construire un robot télécommandé **Lakitu du Futur**.

## Matériel Nécessaire 
- Maya 2024
- Imprimante 3D
- Aluminimum
- Peinture Jaune, Marron et Argenté
- Fil de Fer
- Pistolet à Colle
- Bois fin ou carton épais
  
## Sommaire de Création
1. Création 3D de la coque
      - Récupération d'un modèle
      - Modification du modèle
      - Export des fichiers
      - Impression 3D
2. Assemblage et Personnalisation de la coque
      - Création des accessoires
      - Peinture
      - Assemblage des élements 

## 1. Création 3D de la coque 
La première étape consiste à imaginer et créer la coque de notre robot. 
D'abord, il faut récupérer un modèle 3D sur internet qui convient au niveau de la forme globale au résultat attendu pour notre robot : [Lien vers le modèle](https://cults3d.com/fr/mod%C3%A8le-3d/jeu/lakitu-from-mario-games-multi-color).

Puis, il faut réparer et réadappter un peu le modèle selon nos besoins. Pour ça nous allons utiliser _**Maya**_ qui va nous permettre à retopo le modèle pour que les modifications soient plus simples, et _**Blender**_ pour les modifications des élements, Blender étant un logiciel plus accessible et facile à prendre en main. Il est possible d'utiliser uniquement Maya.  

- D'abord, nous importons et reconstituons le modèle téléchargé depuis Internet, et nous gardons uniquement les élements qui nous intéressent, à savoir le nuage, le corps, la tête, les bras et la carapace. Il faut bien faire attention à ce que le modèle soit à la bonne échelle (à savoir 10cm de large) :
  
Reconstitution du modèle | Eléments intéressants
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/lakitu_og.png?raw=true" width="500">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/lakitu_v2.png?raw=true" width="509.7">

- Puis, nous allons cleaner et reboucher les trous présents dans les mesh. Exemple avec le nuage, on retire les polygones en trop dans les trous, et on rebouche ceux-ci grâce à un *"Fill"*, puis lissez grossièrement les reliefs en mode sculpt grâce au bruch *"Smooth"*. Il faut faire ça aussi avec le corps (où on va retirer la partie basse qui servait de support, et reboucher les bras), et la tête (on rebouche les yeux et le trous au dessus de son crâne) : 
  
Avant | Après
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/nuage_old.png?raw=true" width="450">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/nuage_new.png?raw=true" width="540">

- Pour le bras droit, nous allons tout simplement suprimmer la main, et la remplacer par la main gauche du modèle que nous aurons copié, mis en symétrie, et rattaché au reste du bras droit :

Avant | Après
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/bras_avant%20.png?raw=true" width="445">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/bras_apres.png?raw=true" width="470">

- Puis, nous allons recréer des petits élements, à savoir les yeux et la bouche du nuage (avec des demi-sphères qu'on met à la bonne taille), ainsi que la carapace (qui est aussi une demi sphère) : 

Visage | Carapace
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/nuage_visage.png?raw=true" width="445">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/carapace.png?raw=true" width="470">

