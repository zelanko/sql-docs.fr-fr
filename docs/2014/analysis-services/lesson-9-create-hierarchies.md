---
title: 'Leçon 10 : Créer des hiérarchies | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 51f8d7b6616f6f14621209561146916cb4b0acd1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187286"
---
# <a name="lesson-10-create-hierarchies"></a>Leçon 10 : Créer des hiérarchies
  Dans cette leçon, vous allez créer des hiérarchies. Les hiérarchies sont des groupes de colonnes ordonnées par niveaux ; par exemple, une hiérarchie Geography peut avoir des sous-niveaux Country, State, County et City. Les hiérarchies peuvent apparaître séparément des autres colonnes dans une liste de champs de l'application cliente de création de rapports, ce qui les rend faciles à parcourir par les utilisateurs clients et à inclure dans un rapport. Pour plus d’informations, consultez [Hiérarchies &#40;SSAS Tabulaire&#41;](tabular-models/hierarchies-ssas-tabular.md).  
  
 Pour créer des hiérarchies, vous allez utiliser le concepteur de modèles dans la *Vue du diagramme*. La création et la gestion des hiérarchies n'est pas prise en charge dans le générateur de modèles dans la vue de données.  
  
 Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 9 : Créer des perspectives](lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Créer des hiérarchies  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>Pour créer une hiérarchie de catégorie dans la table Product  
  
1.  Dans le Concepteur de modèles, cliquez sur le `Model` menu, puis pointez sur **vue de modèle**, puis cliquez sur **vue de diagramme**.  
  
    > [!TIP]  
    >  Utilisez les contrôles de la minicarte dans l'angle supérieur droit du concepteur de modèles pour ajuster la vue des objets dans la vue du diagramme. Si vous replacez les objets dans la vue de diagramme, cette vue sera conservée lorsque vous enregistrerez le projet.  
  
2.  Dans le Concepteur de modèles, cliquez sur le `Product` table, puis cliquez sur **créer une hiérarchie**. Une hiérarchie apparaît en bas de la fenêtre de la table.  
  
3.  Dans le nom de la hiérarchie, renommez la hiérarchie en tapant `Category`, puis appuyez sur ENTRÉE.  
  
4.  Dans le `Product` table, cliquez sur le **Product Category Name** colonne, puis faites-le glisser vers le `Category` hiérarchie, puis relâchez la souris sur le `Category` nom.  
  
5.  Dans le `Category` hiérarchie, avec le bouton droit le **Product Category Name** colonne, puis cliquez sur **renommer**, puis tapez `Category`.  
  
    > [!NOTE]  
    >  Renommer une colonne dans une hiérarchie ne renomme pas cette colonne dans la table. Une colonne dans une hiérarchie est simplement une représentation de la colonne dans la table.  
  
6.  Dans le `Product` table, cliquez sur le **Product Subcategory Name** colonne, puis, dans le menu contextuel, pointez sur **ajouter à la hiérarchie**, puis cliquez sur `Category`.  
  
7.  Renommer **Product Subcategory Name** à `Subcategory`.  
  
8.  À l’aide de clic et glisser, ou à l’aide de la **ajouter à la hiérarchie** dans le menu contextuel de commandes, ajoutez le **Nom_modèle** et **Product Name** colonnes (dans l’ordre) et les placer sous le **Product Subcategory Name** colonne. Renommez ces colonnes `Model` et `Product`, respectivement.  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>Pour créer des hiérarchies dans la table Date  
  
1.  Dans le concepteur de modèles, cliquez avec le bouton droit sur la table **Date** , puis cliquez sur **Créer une hiérarchie**.  
  
2.  Renommez la hiérarchie en **Calendar**.  
  
3.  Ajoutez les colonnes suivantes, dans l'ordre, puis renommez-les :  
  
    |colonne|Renommer en :|  
    |------------|----------------|  
    |Calendar Year|Année|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|Jour|  
  
4.  Dans la table **Date** , répétez les étapes ci-dessus, en créant une hiérarchie **Fiscal** , y compris les colonnes suivantes :  
  
    |colonne|Renommer en :|  
    |------------|----------------|  
    |Fiscal Year|Année|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|Jour|  
  
5.  Enfin, dans la table **Date** , répétez les étapes ci-dessus, en créant une hiérarchie **Production Calendar** , comprenant les colonnes suivantes :  
  
    |colonne|Renommer en :|  
    |------------|----------------|  
    |Calendar Year|Année|  
    |Week Number Of Year|Week|  
    |Jour de la semaine|Jour|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 11 : Créer des partitions](lesson-10-create-partitions.md).  
  
  
