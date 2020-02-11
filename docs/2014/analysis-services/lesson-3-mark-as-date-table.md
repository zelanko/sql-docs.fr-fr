---
title: 'Leçon 4 : marquer en tant que table de dates | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26877c4892b050cbf9c8dcc6553530dff513f8fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078787"
---
# <a name="lesson-4-mark-as-date-table"></a>Leçon 4 : Marquer en tant que table de dates
  Dans la lecon 2 : Ajouter des données, vous avez importé une table de dimension nommée DimDate. Vous avez ensuite renommé la table DimDate dans la lecon 3 : Renommer des colonnes, en lui attribuant le nom Date. Alors que dans votre modèle cette table s’appelle désormais Date, elle peut également être désignée par *Table de Date*, car elle contient des données de date et d’heure.  
  
 Quand vous utilisez des fonctions Time Intelligence dans les calculs, par exemple, quand vous créez des mesures, vous devez spécifier les propriétés de la table de date, notamment une *table Date* et une *colonne Date* (identificateur unique) dans cette table. Vous pouvez ensuite créer des relations valides entre d'autres tables et la table de dates, nécessaires pour les calculs qui utilisent les fonctions Time Intelligence DAX.  
  
 Dans cette leçon, vous marquez la table Date importée et renommée comme *Table de Date* et la colonne Date (dans la table de date) comme *Colonne de date* (identificateur unique). Toute utilisation de la date de nom peut devenir confuse, mais vous obtiendrez bientôt l’idée.  
  
 Durée estimée pour suivre cette leçon : **3 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 3 : Renommer des colonnes](rename-columns.md).  
  
### <a name="to-set-mark-as-date-table"></a>Pour marquer en tant que table de dates  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Date** (onglet).  
  
2.  Cliquez sur le menu **Table**, cliquez sur **Date**, puis cliquez sur **Marquer en tant que table de dates**.  
  
3.  Dans la boîte de dialogue **Marquer en tant que table de dates**, dans la zone de liste **Date**, sélectionnez la colonne **Date** comme identificateur unique.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour continuer ce didacticiel, passez à la [Leçon 5 : Créer des relations](lesson-4-create-relationships.md).  
  
  
