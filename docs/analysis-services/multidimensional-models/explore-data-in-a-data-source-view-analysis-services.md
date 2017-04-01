---
title: "Explorer des donn&#233;es dans une vue de source de donn&#233;es (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exploration de données [Analysis Services]"
  - "vues de source de données [Analysis Services], exploration de données"
  - "affichage des données sources"
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Explorer des donn&#233;es dans une vue de source de donn&#233;es (Analysis Services)
  Vous pouvez utiliser la boîte de dialogue **Explorer les données** du Concepteur de vue de source de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour parcourir les données d’une table, d’une vue ou d’une requête nommée dans une vue de source de données (DSV). Si vous explorez les données dans le Concepteur de vue de source de données, vous pouvez afficher le contenu de chacune des colonnes de données d'une table, d'une vue ou d'une requête nommée sélectionnée. Cet affichage vous permet de déterminer si toutes les colonnes sont nécessaires, si des calculs nommés sont nécessaires pour améliorer la convivialité, et si les requêtes nommées ou les calculs nommés existants retournent les valeurs prévues.  
  
 Pour afficher les données, vous devez disposer d'une connexion active aux sources de données pour l'objet sélectionné dans la vue de source de données (DSV). Le cas échéant, tous les calculs nommés d'une table sont également envoyés dans la requête.  
  
 Données retournées dans un format tabulaire que vous pouvez trier et copier. Cliquez sur les en-têtes de colonnes pour re-trier les lignes par cette colonne. Vous pouvez également mettre en surbrillance des données dans la grille et appuyer sur Ctrl+C pour copier la sélection dans le presse-papiers.  
  
 Vous pouvez également contrôler la méthode d'échantillonnage et le nombre d'échantillons. Par défaut, les 5000 premières lignes sont retournées.  
  
## Pour parcourir les données ou modifier les options d'échantillonnage  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou connectez-vous à la base de données qui contient la vue de source de données dans laquelle vous souhaitez explorer les données.  
  
2.  Dans l’Explorateur de solutions, développez le dossier **Vues des sources de données**, puis double-cliquez sur la vue de source de données.  
  
3.  Cliquez avec le bouton droit sur la table, la vue ou la requête nommée contenant les données que vous voulez consulter, puis sélectionnez **Explorer les données**.  
  
     La source de données sous-jacente de la table, de la vue ou de la requête nommée dans la vue de source de données représente des requêtes, et les résultats s’affichent sous l’onglet **Explorer la table \<nom de l’objet>**.  
  
4.  Dans la barre d’outils **Explorer la table \<nom de l’objet>**, cliquez sur l’icône **Options d’échantillonnage**.  
  
     La boîte de dialogue **Options d'exploration de données** s'ouvre. Dans cette boîte de dialogue, vous pouvez spécifier la méthode d’échantillonnage (et augmenter ou diminuer le nombre d’enregistrements par rapport à la taille d’échantillonnage par défaut de 5000 lignes) ou le nombre d’échantillons.  
  
5.  Selon le cas, cliquez sur **OK** ou sur **Annuler** .  
  
6.  Pour rééchantillonner les données, cliquez sur **Rééchantillonner des données** dans la barre d’outils **Explorer la table \<nom de l’objet>**.  
  
## Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  