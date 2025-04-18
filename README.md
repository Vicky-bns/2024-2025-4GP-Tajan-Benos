# 2024-2025-4GP-Tajan-Benos-Projet Capteur Graphite

## SOMMAIRE
*** 
  - [I. Description Projet Graphite](#Description-Projet-Graphite)
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

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Dans le cadre de l’UE "Du capteur au banc de test" en 4e année de Génie Physique à l’INSA Toulouse, nous avons développé un capteur de contrainte basé sur une technologie low-tech. Ce capteur utilise du graphite déposé sur une feuille de papier à l’aide d’un crayon. Lorsqu’on applique une déformation au papier, la structure du graphite change, ce qui modifie ses propriétés électriques, comme la résistance. Ce capteur low-tech fonctionne sur le principe de la percolation dans un réseau de nanoparticules de graphite déposé sur une feuille de papier. Le transport des électrons se fait par effet tunnel entre les particules. Lorsqu'une déformation est appliquée, la distance entre les particules varie. En extension, certains chemins de conduction sont interrompus, augmentant la résistance. En compression, la distance diminue, créant de nouveaux chemins et réduisant la résistance. La jauge de contrainte mesure ces variations de résistance pour déterminer la déformation et la contrainte appliquées.
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

## Electronique Analogique sous LTSpice


