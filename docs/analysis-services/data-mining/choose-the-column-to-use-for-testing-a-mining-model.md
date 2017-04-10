---
title: "Choisir la colonne &#224; utiliser pour tester un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colonnes [exploration de données], colonnes prédictibles de l’exploration de données"
  - "graphique d’analyse de précision de l’exploration de données [Analysis Services], colonnes"
  - "colonnes d'exploration de données prévisibles [Analysis Services]"
ms.assetid: c6a8f23a-da21-4f31-9521-99460d624649
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 35
---
# Choisir la colonne &#224; utiliser pour tester un mod&#232;le d&#39;exploration de donn&#233;es
  Avant de pouvoir mesurer la précision d'un modèle d'exploration de données, vous devez déterminer le résultat que vous voulez évaluer. La plupart des modèles d'exploration de données requièrent que vous choisissiez au moins une colonne à utiliser comme attribut prédictible lorsque vous créez le modèle. Par conséquent, lorsque vous testez la précision du modèle, vous devez généralement sélectionner cet attribut comme devant être testé.  
  
 La liste suivante décrit des points supplémentaires à prendre en considération pour choisir l'attribut prédictible à utiliser dans le test :  
  
-   Certains types de modèles d'exploration de données peuvent prédire plusieurs attributs, comme les réseaux neuronaux qui peuvent explorer les relations entre de nombreuses attributs.  
  
-   D'autres types de modèles d'exploration de données, tels que les modèles de clustering, n'ont pas nécessairement un attribut prédictible. Les modèles de clustering ne peuvent être testés que s'ils ont un attribut prédictible.  
  
-   Créer un nuage de points ou mesurer la précision d'un modèle de régression requiert que vous choisissiez un attribut prédictible continu comme résultat. Dans ce cas, vous ne pouvez pas spécifier une valeur cible. Si vous créez autre chose qu’un nuage de points, la colonne de structure d’exploration de données sous-jacente doit également avoir un type de contenu **Discret** ou **Discrétisé**.  
  
-   Si vous choisissez un attribut discret comme résultat prédictible, vous pouvez également spécifier une valeur cible, ou vous pouvez laisser le champ **Prédire la valeur** vide. Si vous renseignez le champ **Prédire la valeur**, le graphique mesure uniquement l’efficacité du modèle dans la prédiction de la valeur cible. Si vous ne spécifiez pas de résultat cible, le modèle est mesuré pour sa précision dans la prédiction de tous les résultats.  
  
-   Si vous voulez inclure plusieurs modèles et les comparer dans un graphique d'analyse de précision unique, tous les modèles doivent utiliser la même colonne prédictible.  
  
-   Quand vous créez un rapport de validation croisée, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] analyse automatiquement tous les modèles qui ont le même attribut prédictible.  
  
-   Quand l’option **Synchroniser les colonnes de prédiction et les valeurs** est sélectionnée, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] choisit automatiquement les colonnes prédictibles ayant le même nom et des types de données correspondants. Si vos colonnes ne répondent pas à ces critères, vous pouvez désactiver cette option et choisir manuellement une colonne prédictible. Vous devrez peut-être le faire si vous testez le modèle avec un jeu de données externes qui n'a pas les mêmes colonnes que le modèle. Toutefois, si vous choisissez une colonne dont le type de données est incorrect, vous obtiendrez une erreur ou des résultats incorrects.  
  
### Spécifier le résultat à prédire  
  
1.  Double-cliquez sur la structure d'exploration de données pour l'ouvrir dans le Concepteur d'exploration de données.  
  
2.  Sélectionnez l’onglet **Graphique d’analyse de précision de l’exploration de données**.  
  
3.  Sélectionnez l’onglet **Sélection d’entrée**.  
  
4.  Sous l’onglet **Sélection d’entrée**, sous **Nom de la colonne prédictible**, sélectionnez une colonne prédictible pour chaque modèle que vous incluez dans le graphique.  
  
     Les colonnes du modèle d’exploration de données qui sont disponibles dans la zone **Nom de la colonne prédictible** sont uniquement celles dont le type d’utilisation est **Prédire** ou **Prédire uniquement**.  
  
5.  Si vous souhaitez déterminer l’élévation pour un modèle, vous devez sélectionner une valeur de résultat spécifique à mesurer dans la liste **Prédire la valeur**.  
  
## Voir aussi  
 [Choisir et mapper les données de test du modèle](../../analysis-services/data-mining/choose-and-map-model-testing-data.md)   
 [Choisir un type de graphique d'analyse de précision et définir des options de graphique](../../analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  