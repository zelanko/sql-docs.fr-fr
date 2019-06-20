---
title: 'Leçon 11 : Créer des Partitions | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 06ffe60802e52bd0ae141435628fc3812dc2c7c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66079198"
---
# <a name="lesson-11-create-partitions"></a>Leçon 11 : Créer des partitions
  Dans cette leçon, vous allez créer des partitions pour diviser la table Internet Sales en parties logiques plus petites pouvant être traitées (actualisées) indépendamment d'autres partitions. Par défaut, chaque table que vous incluez dans votre modèle comporte une partition qui inclut toutes les colonnes et les lignes de la table. Pour la table Internet Sales, nous souhaitons diviser les données par année ; une seule partition pour chacune des cinq années de la table.  Chaque partition peut ensuite être traitée indépendamment. Pour plus d’informations, consultez [Partitions &#40;SSAS Tabulaire&#41;](tabular-models/partitions-ssas-tabular.md).  
  
 Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 10 : Créer des hiérarchies](lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Créer des partitions  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a>Pour créer des partitions dans la table Internet Sales  
  
1.  Dans le Générateur de modèles, cliquez sur la table **Internet Sales** , sur le menu **Table** , puis sur **Partitions**.  
  
     La boîte de dialogue **Gestionnaire de partition** s’ouvre.  
  
2.  Dans le **le Gestionnaire de Partition** boîte de dialogue **Partitions**, cliquez sur le **Internet Sales** partition.  
  
3.  Dans **nom de la Partition**, remplacez le nom par `Internet Sales 2005`.  
  
    > [!TIP]  
    >  Avant de passer à l'étape suivante, notez que les noms des colonnes dans la fenêtre d'aperçu de la table affichent les colonnes incluses dans la table modèle (activée) avec les noms des colonnes de la source. Cela est dû au fait que la fenêtre d'aperçu de la table affiche les colonnes de la table source, pas de la table modèle.  
  
4.  Sélectionnez le bouton **Éditeur de requête** au-dessus du côté droit de la fenêtre d’aperçu.  
  
     Étant donné que vous souhaitez que la partition inclue uniquement les lignes appartenant à une certaine période, vous devez inclure une clause WHERE. Vous pouvez créer une clause WHERE uniquement à l'aide d'une instruction SQL.  
  
5.  Dans le champ **Instruction SQL** , remplacez l’instruction existante en collant l’instruction suivante :  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     Cette instruction spécifie que la partition doit inclure toutes les données des lignes où OrderDate correspond à l'année calendaire 2005 tel que spécifié dans la clause WHERE.  
  
6.  Cliquez sur **Valider**.  
  
     Notez qu'un avertissement s'affiche indiquant que certaines colonnes ne sont pas présentes dans la source. Il s’agit, car dans [leçon 3 : Renommer des colonnes](rename-columns.md), vous avez renommé ces colonnes dans la table Internet Sales dans le modèle soit différent de ces mêmes colonnes au niveau de la source.  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a>Pour créer une partition pour l’année 2006 dans la table Internet Sales  
  
1.  Dans le **le Gestionnaire de Partition** boîte de dialogue **Partitions**, cliquez sur le `Internet Sales 2005` partition que vous venez de créer, puis **copie**.  
  
2.  Dans **nom de la Partition**, type `Internet Sales 2006`.  
  
3.  Dans l’instruction SQL, dans l’ordre pour la partition inclue uniquement les lignes pour l’année 2006, remplacez la clause WHERE avec les éléments suivants :  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a>Pour créer une partition pour l’année 2007 dans la table Internet Sales  
  
1.  Dans la boîte de dialogue **Gestionnaire de partition** , cliquez sur **Copier**.  
  
2.  Dans **nom de la Partition**, type `Internet Sales 2007`.  
  
3.  Dans **basculer vers**, sélectionnez **éditeur de requête**.  
  
4.  Dans l’instruction SQL, dans l’ordre pour la partition inclue uniquement les lignes pour l’année 2007, remplacez la clause WHERE avec les éléments suivants :  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a>Pour créer une partition pour l’année 2008 dans la table Internet Sales  
  
1.  Dans la boîte de dialogue **Gestionnaire de partition** , cliquez sur **Nouveau**.  
  
2.  Dans **nom de la Partition**, type `Internet Sales 2008`.  
  
3.  Dans **basculer vers**, sélectionnez **éditeur de requête**.  
  
4.  Dans l’instruction SQL, dans l’ordre pour la partition inclue uniquement les lignes de l’année 2008, remplacez la clause WHERE avec les éléments suivants :  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a>Pour créer une partition pour l'année 2009 dans la table Internet Sales  
  
1.  Dans la boîte de dialogue **Gestionnaire de partition** , cliquez sur **Nouveau**.  
  
2.  Dans **nom de la Partition**, type `Internet Sales 2009`.  
  
3.  Dans **basculer vers**, sélectionnez **éditeur de requête**.  
  
4.  Dans l'instruction SQL, pour que la partition inclue uniquement les lignes pour l'année 2009, remplacez la clause WHERE par :  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a>Traiter les partitions  
 Dans la boîte de dialogue **Gestionnaire de partition** , notez l’astérisque (**\***) en regard des noms de partition pour chacune des partitions que vous venez de créer. Cela indique que la partition n'a pas été traitée (actualisée). Lorsque vous créez de nouvelles partitions, vous devez exécuter une opération « Traiter les partitions » ou « Traiter la table » pour actualiser les données dans ces partitions.  
  
#### <a name="to-process-internet-sales-partitions"></a>Pour traiter les partitions Internet Sales  
  
1.  Cliquez sur **OK** pour fermer la boîte de dialogue **Gestionnaire de partition** .  
  
2.  Dans le Concepteur de modèles, cliquez sur la table **Internet Sales** , cliquez sur le menu **Modèle** , puis pointez sur **Traiter** (Actualiser) et enfin, cliquez sur **Traiter les partitions**.  
  
3.  Dans la boîte de dialogue **Traiter les partitions** , vérifiez que le **Mode** est défini sur **Traiter par défaut**.  
  
4.  Cochez la case dans la colonne **Traiter** pour chacune des cinq partitions que vous avez créées, puis cliquez sur **OK**.  
  
     Si vous êtes invité à fournir les informations d'emprunt d'identité, entrez le nom d'utilisateur Windows et le mot de passe spécifiés dans la leçon 2, étape 6.  
  
     Le **données processus** boîte de dialogue s’affiche, puis affiche les détails du processus pour chaque partition. Notez qu'un nombre de lignes différent est transféré pour chaque partition. Cela est dû au fait que chaque partition contient uniquement les lignes de l'année spécifiée dans la clause WHERE dans l'instruction SQL. Il n'y a pas de données pour l'année 2010.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour continuer ce didacticiel, passez à la leçon suivante : Leçon : [Leçon 12 : Créer des rôles](lesson-11-create-roles.md).  
  
  
