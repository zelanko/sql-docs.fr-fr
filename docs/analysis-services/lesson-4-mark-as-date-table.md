---
title: "Le&#231;on&#160;4&#160;: Marquer en tant que table de dates | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;4&#160;: Marquer en tant que table de dates
Dans la Leçon 2 : Ajouter des données, vous avez importé une table de dimension nommée DimDate et l’avez renommée en Date. Alors que dans votre modèle cette table s’appelle désormais Date, elle peut également être désignée par *Table de Date*, car elle contient des données de date et d’heure.  
  
Quand vous utilisez des fonctions Time Intelligence dans les calculs, par exemple, quand vous créez des mesures, vous devez spécifier les propriétés de la table de date, notamment une *table Date* et une *colonne Date* (identificateur unique) dans cette table. Vous pouvez ensuite créer des relations valides entre d'autres tables et la table de dates, nécessaires pour les calculs qui utilisent les fonctions Time Intelligence DAX.  
  
Dans cette leçon, vous marquez la table Date importée et renommée comme *Table de Date* et la colonne Date (dans la table de date) comme *Colonne de date* (identificateur unique). L'utilisation du nom Date peut générer une confusion, vous allez bientôt comprendre pourquoi.  
  
Durée estimée pour effectuer cette leçon : **3 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 3 : Renommer des colonnes](../analysis-services/lesson-3-rename-columns.md).  
  
### Pour définir Marquer en tant que table de dates  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Date ** (onglet).  
  
2.  Sélectionnez la colonne **Date**, puis dans la fenêtre **Propriétés**, sous **Type de données**, vérifiez que **Date** est sélectionné.  
  
3.  Cliquez sur le menu **Table**, cliquez sur **Date**, puis sur **Marquer comme Table de Date**.  
  
4.  Dans la boîte de dialogue **Marquer comme Table de Date**, dans la zone de liste **Date**, sélectionnez la colonne **Date**comme identificateur unique.  
  
## Étapes suivantes  
Pour continuer ce didacticiel, passez à la [Leçon 5 : Créer des relations](../analysis-services/lesson-5-create-relationships.md).  
  
  
  
