---
title: "Sp&#233;cifier la marque comme table de dates pour l&#39;utiliser avec Time Intelligence (SSAS - Tabulaire) | Microsoft Docs"
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
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Sp&#233;cifier la marque comme table de dates pour l&#39;utiliser avec Time Intelligence (SSAS - Tabulaire)
  Pour utiliser des fonctions Time Intelligence dans les formules DAX, vous devez spécifier une table de dates et une colonne (datetime) d'identification unique pour le type de données Date. Une fois qu'une colonne dans la table de dates est spécifiée comme identificateur unique, vous pouvez créer des relations entre les colonnes de cette table et de toutes les tables de faits.  
  
 Lorsque vous utilisez les fonctions Time Intelligence, les règles suivantes s'appliquent :  
  
-   Lorsque vous utilisez les fonctions Time Intelligence DAX, ne spécifiez jamais une colonne datetime à partir d'une table de faits. Créez toujours une table de dates distincte dans votre modèle, avec au moins une colonne datetime de type de données Date et avec des valeurs uniques.  
  
-   Vérifiez que votre table de dates a une plage de dates continue.  
  
-   La colonne datetime dans la table de dates doit avoir une granularité de jour (sans fractions d'un jour).  
  
-   Vous devez spécifier une table de dates et une colonne d'identificateur unique à l'aide de la boîte de dialogue **Marquez la table de dates** .  
  
-   Créez des relations entre les tables de faits et les colonnes de type de données Date dans la table de dates.  
  
#### Pour spécifier une table de dates et un identificateur unique  
  
1.  Dans le concepteur de modèles, cliquez sur la table de dates.  
  
2.  Cliquez sur le menu **Table** , cliquez sur **Date**, puis cliquez sur **Marquer en tant que table de dates**  
  
3.  Dans la boîte de dialogue **Marquer en tant que table de dates** , dans la zone de liste **Date** , sélectionnez une colonne à utiliser comme identificateur unique. Cette colonne doit contenir des valeurs uniques et doit avoir le type de données Date. Par exemple :  
  
    |Date|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  Si nécessaire, créez les relations entre les tables de faits et la table de dates.  
  
## Voir aussi  
 [Calculs &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [Fonctions Time Intelligence (DAX)](http://msdn.microsoft.com/fr-fr/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  