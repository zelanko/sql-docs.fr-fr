---
title: 'Leçon du didacticiel Analysis Services 3 : marquer en tant que Table de dates | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82b4093aa1a46cf1a7bb14b4c689ba6ba09e4d2b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973166"
---
# <a name="mark-as-date-table"></a>Marquer en tant que table de dates

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans la leçon 2 : Obtenir des données, vous avez importé une table de dimension nommée **DimDate**. Alors que dans votre modèle cette table est nommée DimDate, elle peut également être appelée un *table de dates*, car il contient des données de date et d’heure.  
  
Chaque fois que vous utilisez les fonctions time intelligence DAX, comme lorsque vous créez des mesures plus tard, vous devez spécifier les propriétés qui incluent un *table de dates* et un identificateur unique *colonne de Date* dans cette table.
  
Dans cette leçon, vous marquez le **DimDate** table en tant que le *table de dates* et **Date** colonne (dans la table de dates) en tant que le *colonne de Date* (unique identificateur).  

Avant de marquer la table de date et d’une colonne de date, il est judicieux de faire quelques modifications visant à faciliter la compréhension de votre modèle. Notez que, dans la table DimDate, une colonne nommée **FullDateAlternateKey**. Cette colonne contient une ligne pour chaque jour de chaque année civile incluse dans la table. Vous utilisez cette colonne beaucoup dans les formules de mesure et dans les rapports. Cependant, FullDateAlternateKey n’est pas vraiment un bon identificateur pour cette colonne. Renommez cette colonne **Date**, rendant ainsi plus faciles à identifier et à inclure dans les formules. Si possible, il est judicieux de renommer des objets tels que des tables et des colonnes pour les rendre plus facilement repérable dans SSDT et création de rapports des applications clientes. 
  
Durée estimée pour effectuer cette leçon : **trois minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [leçon 2 : obtenir des données](../tutorial-tabular-1400/as-lesson-2-get-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Pour renommer la colonne FullDateAlternateKey

1.  Dans le Concepteur de modèles, cliquez sur le **DimDate** table.

2.  Double-cliquez sur l’en-tête pour le **FullDateAlternateKey** colonne, puis renommez-le à **Date**.

  
### <a name="to-set-mark-as-date-table"></a>Pour définir Marquer en tant que table de dates  
  
1.  Sélectionnez la colonne **Date** , puis dans la fenêtre **Propriétés** , sous **Type de données**, vérifiez que  **Date** est sélectionné.  
  
2.  Cliquez sur le menu **Table** , cliquez sur **Date**, puis sur **Marquer comme Table de Date**.  
  
3.  Dans la boîte de dialogue **Marquer comme Table de Date** , dans la zone de liste **Date** , sélectionnez la colonne **Date** comme identificateur unique. Il est généralement sélectionné par défaut. Cliquez sur **OK**. 

    ![en tant que-lesson3-date-table](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 4 : Créer des relations](../tutorial-tabular-1400/as-lesson-4-create-relationships.md).
  
