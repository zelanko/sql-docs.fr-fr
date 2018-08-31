---
title: 'Leçon 3 : Marquer en tant que Table de dates | Microsoft Docs'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cb63b6cb67303dd763263b7d9dbeea30cfc4e3b
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42791980"
---
# <a name="lesson-3-mark-as-date-table"></a>Leçon 3 : Marquer en tant que table de dates
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Dans la lecon 2 : Ajouter des données, vous avez importé une table de dimension nommée DimDate. Alors que dans votre modèle cette table est nommée DimDate, elle peut également être appelée un *table de dates*, car il contient des données de date et d’heure.  
  
Chaque fois que vous utilisez des fonctions time intelligence DAX dans les calculs, lorsque vous effectuerez lorsque vous créez des mesures un peu plus tard, vous devez spécifier des propriétés de table de date, qui incluent un *table de dates* et un identificateur unique *Date colonne* dans cette table.
  
Dans cette leçon, vous allez marquer la table DimDate comme le *table de dates* et la colonne de Date (dans la table de dates) en tant que le *colonne de Date* (identificateur unique).  

Avant de nous marquer la table de date et d’une colonne de date, nous devons faire un peu de ménage pour faciliter la compréhension de notre modèle. Vous remarquerez que dans la table DimDate à une colonne nommée **FullDateAlternateKey**. Il contient une ligne pour chaque jour de chaque année civile incluse dans la table. Nous allons utiliser cette colonne très souvent dans les formules de mesure et dans les rapports. Mais, FullDateAlternateKey n’est pas vraiment un bon identificateur pour cette colonne. Nous allons le renommer **Date**, rendant ainsi plus faciles à identifier et à inclure dans les formules. Si possible, il est judicieux de renommer des objets tels que des tables et des colonnes pour les rendre plus facilement repérable dans la création de rapports tels que Power BI et Excel, les applications clientes. 
  
Durée estimée pour effectuer cette leçon : **3 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [leçon 2 : ajouter des données](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Pour renommer la colonne FullDateAlternateKey

1.  Dans le Concepteur de modèles, cliquez sur le **DimDate** table.

2.  Double-cliquez sur l’en-tête pour le **FullDateAlternateKey** colonne, puis renommez-le à **Date**.

  
### <a name="to-set-mark-as-date-table"></a>Pour définir Marquer en tant que table de dates  
  
1.  Sélectionnez la colonne **Date** , puis dans la fenêtre **Propriétés** , sous **Type de données**, vérifiez que  **Date** est sélectionné.  
  
2.  Cliquez sur le menu **Table** , cliquez sur **Date**, puis sur **Marquer comme Table de Date**.  
  
3.  Dans la boîte de dialogue **Marquer comme Table de Date** , dans la zone de liste **Date** , sélectionnez la colonne **Date** comme identificateur unique. Celle-ci est généralement être sélectionnée par défaut. Cliquez sur **OK**. 

    ![en tant que-tabulaire-lesson3-date-table](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quelle est l’étape suivante ?
Accédez à la leçon suivante : [leçon 4 : créer des relations](../analysis-services/lesson-4-create-relationships.md).
  
