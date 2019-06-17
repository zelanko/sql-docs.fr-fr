---
title: 'Analysis Services leçon du didacticiel 9 : Créer des hiérarchies | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 92f83e1e2b3553f85301574e98f95ed7e22c1184
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148976"
---
# <a name="create-hierarchies"></a>Créer des hiérarchies

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez des hiérarchies. Les hiérarchies sont des groupes de colonnes organisées en niveaux. Par exemple, une hiérarchie géographie peut comporter des sous-niveaux pour pays, état, comté et ville. Les hiérarchies peuvent apparaître séparément des autres colonnes dans une liste de champs de l'application cliente de création de rapports, ce qui les rend faciles à parcourir par les utilisateurs clients et à inclure dans un rapport. Pour plus d’informations, consultez [hiérarchies](../tabular-models/hierarchies-ssas-tabular.md)
  
Pour créer des hiérarchies, utilisez le Générateur de modèles dans *vue de diagramme*. Création et la gestion des hiérarchies ne sont pas pris en charge dans la vue de données.  
  
Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 8 : Créer des perspectives](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Créer des hiérarchies  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Pour créer une hiérarchie de catégorie dans la table DimProduct  
  
1.  Dans le Générateur de modèles (vue de diagramme), cliquez sur le **DimProduct** table > **créer une hiérarchie**. Une hiérarchie apparaît en bas de la fenêtre de la table. Renommez la hiérarchie **catégorie**.  
  
2.  Cliquez et faites glisser le **ProductCategoryName** colonne vers la nouvelle **catégorie** hiérarchie.  
  
3.  Dans le **catégorie** hiérarchie, avec le bouton droit **ProductCategoryName** > **renommer**, puis tapez **catégorie**.  
  
    > [!NOTE]  
    > Renommer une colonne dans une hiérarchie ne renomme pas cette colonne dans la table. Une colonne dans une hiérarchie est simplement une représentation de la colonne dans la table.  
  
4.  Cliquez et faites glisser le **ProductSubcategoryName** colonne à la **catégorie** hiérarchie. Renommez-le **sous-catégorie**. 
  
5.  Avec le bouton droit le **ModelName** colonne > **ajouter à la hiérarchie**, puis sélectionnez **catégorie**. Renommez-le **modèle**.

6.  Enfin, ajoutez **EnglishProductName** à la hiérarchie de catégorie. Renommez-le **produit**.  

    ![as-lesson9-category](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Pour créer des hiérarchies dans la table DimDate  
  
1.  Dans le **DimDate** table, créez une hiérarchie nommée **calendrier**.  
  
3.  Ajoutez l’ordre des colonnes suivantes :

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  Dans le **DimDate** table, créez un **Fiscal** hiérarchie. Inclure l’ordre des colonnes suivantes :  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Enfin, dans le **DimDate** table, créez un **ProductionCalendar** hiérarchie. Inclure l’ordre des colonnes suivantes :  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 10 : Créer des partitions](../tutorial-tabular-1400/as-lesson-10-create-partitions.md). 
  
  
