# 2024-2025-4GP-Tajan-Benos-Projet Capteur Graphite

## SOMMAIRE
*** 
  - [I. Description Projet Graphite](#description-projet-draphite)
  - [II. Livrables](#livrables)
  - [III. Matériel nécessaire](#matériel-nécessaire)
  - [IV. Electronique Analogique sous LTSpice](#electronique-analogique-sous-ltspice)
  - [V. Création du PCB sous KiCad](#creation-du-pcb-sous-kicad)
  - [VI. Code Arduino](#code-arduino)
  - [VII. Application Android](#application-android)
  - [VIII. Réalisation du shield](#réalisation-du-shield)
  - [IX. Banc de tests](#banc-de-tests)
  - [X. Datasheet](#datasheet)

*** 

## Description Projet Graphite

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Dans le cadre de l’UE "Du capteur au banc de test" en 4e année de Génie Physique à l’INSA Toulouse, nous avons développé un capteur de contrainte basé sur une technologie low-tech. Ce capteur utilise du graphite déposé sur une feuille de papier à l’aide d’un crayon. Lorsqu’on applique une déformation au papier, la structure du graphite change, ce qui modifie ses propriétés électriques, comme la résistance. Ce capteur low-tech fonctionne sur le principe de la percolation dans un réseau de nanoparticules de graphite déposé sur une feuille de papier. Le transport des électrons se fait par effet tunnel entre les particules. Lorsqu'une déformation est appliquée, la distance entre les particules varie. En extension, certains chemins de conduction sont interrompus, augmentant la résistance. En compression, la distance diminue, créant de nouveaux chemins et réduisant la résistance. La jauge de contrainte mesure ces variations de résistance pour déterminer la déformation et la contrainte appliquées. \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Le projet a consisté à développer un système complet autour de ce capteur : modélisation d'électronique analogique, création d’un circuit imprimé (PCB), programmation avec Arduino, ajout d’une interface utilisateur (écran OLED, encodeur, etc.) et communication sans fil via Bluetooth pour une application mobile. Un banc de test a été réalisé pour évaluer les performances du capteur à l'aide d'un banc de mesure réalisé en 3D. L’ensemble du travail a abouti à la rédaction d’une datasheet, décrivant les caractéristiques du capteur.

## Livrables

  - Shield PCB compatible Arduino UNO, intégrant un capteur graphite, un amplificateur transimpédance, un module Bluetooth, un écran OLED, un flex sensor, un potentiomètre digital et un encodeur rotatoire
  - Code Arduino assurant la lecture du capteur, l’affichage des données, la communication Bluetooth et l’interaction avec les composants
  - Application Android réalisée sous MIT App Inventor pour visualiser les mesures transmises par Bluetooth
  - Banc de test utilisé pour caractériser le capteur et valider son fonctionnement
  - Datasheet du capteur de contrainte, présentant ses principales caractéristiques et résultats expérimentaux

## Matériel nécessaire

  - 1 carte Arduino Uno
  - 2 Résistance de 100kΩ
  - 1 Résistance de 1kΩ
  - 1 Potentiomètre digital MCP-41050
  - 2 Condensateurs 100nF
  - 1 Condensateurs 1µF
  - 1 Amplificateur LTC1050
  - 1 Écran OLED01
  - 1 Module Bluetooth HC-05
  - 1 encodeur rotatoire 

## Electronique Analogique sous LTSpice

Notre capteur en graphite présente une résistance de l’ordre du gigaohm, ce qui génère un courant de quelques pico- à nanoampères sous une tension de 5 V. Pour rendre ce signal exploitable par l’ADC d’une Arduino UNO, nous avons conçu un amplificateur transimpédance autour de l’AOP LTC1050, il a une très faible dérive et un excellent décalage d’offset. Après avoir modélisé le capteur et le montage sous LTspice pour de déterminer la meilleure valeur de la résistance de rétroaction, nous avons ajouté trois étages de filtrage afin d'améliorer la qualité du signal :  
   1- Filtre passe-bas à 16 Hz (R1–C1) pour éliminer les hautes fréquences parasites,  
   2- Filtre passe-bas à 1,6 Hz (R4–C2) pour atténuer le bruit secteur à 50 Hz,  
   3- Filtre passe-bas à 1,6 kHz (R5–C3) pour supprimer les interférences liées à l’ADC.  

Ce circuit convertit ainsi le faible courant issu du capteur en une tension propre, directement lisible et traitable par la carte Arduino.

Mettre schéma montage LTSpice et Graphe simulation des filtres.


## Création du PCB sous KiCad

Lors de la phase de conception du shield, nous avons d’abord repris le gabarit d’une carte Arduino UNO dans KiCad (version 7.0) pour garantir une compatibilité mécanique et électrique. Après avoir listé tous les éléments dont nous avions besoin, nous avons créé dans KiCad, les symboles et empreintes manquants en respectant leurs dimensions et l’écartement des broches. Voici le schéma électrique de l'ensemble de notre montage :

<p align="center">
<img src="https://github.com/MOSH-Insa-Toulouse/2023-2024-4GP_MANENT_ZUPPELLI/blob/main/images_projet_capteur/capteur_%C3%A0_jauge_de_contrainte.PNG" alt="Figure 1 - Capteur à jauge de contrainte à base de crayon graphite">
<br>
<i>Capteur à jauge de contrainte à base de crayon graphite</i>
</p>

Une fois notre bibliothèque faites, nous avons assemblé le schéma électrique complet : chaque composant est relié selon le fonctionnement prévu. Cette étape nous a permis de vérifier que l’ensemble des composants tenait bien sur la zone réservée au Shield. En passant à la vue PCB, nous avons effectué le routage des pistes dans le but d'une organisation optimal puis ajouté un plan de masse pour améliorer la stabilité et réduire les interférences. 
Voici notre PCB :

Le résultat est un circuit imprimé prêt à être fabriqué et, une fois soudés, à recevoir chaque composant sur le shield Arduino UNO.

