---
title: 'Leçon 4 : Marquer en tant que Table de dates | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ef1be7d87012b6ae1d1b69e3f2c92dccca86ac0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62729195"
---
# <a name="lesson-4-mark-as-date-table"></a>Leçon 4 : Marquer en tant que table de dates
  Dans la leçon 2 : Ajouter des données, vous avez importé une table de dimension nommée DimDate. Ensuite, vous avez renommé la table DimDate, dans la leçon 3 : Renommer des colonnes, simplement, de date. Alors que dans votre modèle cette table s’appelle désormais Date, elle peut également être désignée par *Table de Date*, car elle contient des données de date et d’heure.  
  
 Quand vous utilisez des fonctions Time Intelligence dans les calculs, par exemple, quand vous créez des mesures, vous devez spécifier les propriétés de la table de date, notamment une *table Date* et une *colonne Date* (identificateur unique) dans cette table. Vous pouvez ensuite créer des relations valides entre d'autres tables et la table de dates, nécessaires pour les calculs qui utilisent les fonctions Time Intelligence DAX.  
  
 Dans cette leçon, vous marquez la table Date importée et renommée comme *Table de Date* et la colonne Date (dans la table de date) comme *Colonne de date* (identificateur unique). L’utilisation du nom que date peut générer une confuse, mais vous allez bientôt l’idée.  
  
 Durée estimée pour effectuer cette leçon : **3 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 3 : Renommer des colonnes](rename-columns.md).  
  
### <a name="to-set-mark-as-date-table"></a>Pour définir Marquer en tant que table de dates  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Date** (onglet).  
  
2.  Cliquez sur le menu **Table**, cliquez sur **Date**, puis sur **Marquer comme Table de Date**.  
  
3.  Dans la boîte de dialogue **Marquer comme Table de Date** , dans la zone de liste **Date** , sélectionnez la colonne **Date** comme identificateur unique.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 5 : Créer des relations](lesson-4-create-relationships.md).  
  
  
