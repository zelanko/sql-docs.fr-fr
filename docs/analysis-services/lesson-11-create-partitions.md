---
title: "Le&#231;on&#160;11&#160;: Cr&#233;er des partitions | Microsoft Docs"
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
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;11&#160;: Cr&#233;er des partitions
Dans cette leçon, vous allez créer des partitions pour diviser la table Internet Sales en parties logiques plus petites pouvant être traitées (actualisées) indépendamment d'autres partitions. Par défaut, chaque table que vous incluez dans votre modèle a une partition qui comprend toutes les lignes et colonnes de la table. Pour la table Internet Sales, nous souhaitons diviser les données par année ; une partition pour tous les cinq ans de la table.  Chaque partition peut ensuite être traitée indépendamment. Pour plus d’informations, consultez [Partitions &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 10 : Créer des hiérarchies](../analysis-services/lesson-10-create-hierarchies.md).  
  
## Créer des partitions  
  
#### Pour créer des partitions dans la table Internet Sales  
  
1.  Dans le Générateur de modèles, cliquez sur la table **Internet Sales**, sur le menu **Table**, puis sur **Partitions**.  
  
    La boîte de dialogue **Gestionnaire de partition** s’ouvre.  
  
2.  Dans la boîte de dialogue **Gestionnaire de partition**, dans la liste des partitions, cliquez sur la partition **Internet Sales**.  
  
3.  Dans **Nom de la partition**, changez le nom en **Internet Sales 2010**.  
  
    > [!TIP]  
    > Avant de passer à l'étape suivante, notez que les noms des colonnes dans la fenêtre d'aperçu de la table affichent les colonnes incluses dans la table modèle (activée) avec les noms des colonnes de la source. Cela est dû au fait que la fenêtre d'aperçu de la table affiche les colonnes de la table source, pas de la table modèle.  
  
4.  Sélectionnez le bouton **Éditeur de requête** au-dessus du côté droit de la fenêtre d’aperçu.  
  
    Étant donné que vous souhaitez que la partition inclue uniquement les lignes appartenant à une certaine période, vous devez inclure une clause WHERE. Vous pouvez créer une clause WHERE uniquement à l'aide d'une instruction SQL.  
  
5.  Dans le champ **Instruction SQL**, remplacez l’instruction existante en collant l’instruction suivante :  
  
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
    WHERE (([OrderDate] >= N'2010-01-01 00:00:00') AND ([OrderDate] < N'2011-01-01 00:00:00'))  
    ```  
  
    Cette instruction spécifie que la partition doit inclure toutes les données des lignes où OrderDate correspond à l’année calendaire 2010, comme spécifié dans la clause WHERE.  
  
6.  Cliquez sur **Valider**.  
  
  
#### Pour créer une partition pour l’année 2011  
  
1.  Dans la liste des partitions, cliquez sur la partition **Internet Sales 2010** que vous venez de créer, puis cliquez sur **Copier**.  
  
2.  Dans **Nom de la partition**, tapez **Internet Sales 2011**.  
  
3.  Dans l’instruction SQL, pour que la partition inclue uniquement les lignes pour l’année 2011, remplacez la clause WHERE par :  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### Pour créer une partition pour l’année 2012  
  
1.  Dans la boîte de dialogue **Gestionnaire de partition**, cliquez sur **Copier**.  
  
2.  Dans **Nom de la partition**, tapez **Internet Sales 2012**.  
  
3.  Dans l’instruction SQL, pour que la partition inclue seulement les lignes pour l’année 2012, remplacez la clause WHERE par :  
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### Pour créer une partition pour l’année 2013  
  
1.  Dans la boîte de dialogue **Gestionnaire de partition**, cliquez sur **Nouveau**.  
  
2.  Dans **Nom de la partition**, tapez **Internet Sales 2013**.  
  
3.  Dans l’instruction SQL, pour que la partition inclue seulement les lignes pour l’année 2013, remplacez la clause WHERE par :  
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### Pour créer une partition pour l’année 2014 dans la table Internet Sales  
  
1.  Dans la boîte de dialogue **Gestionnaire de partition**, cliquez sur **Nouveau**.  
  
2.  Dans **Nom de la partition**, tapez **Internet Sales 2014**.  
  
3.  Dans l’instruction SQL, pour que la partition inclue seulement les lignes pour l’année 2014, remplacez la clause WHERE par :  
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  
  
## Traiter les partitions  
Dans la boîte de dialogue **Gestionnaire de partition**, notez l’astérisque (**\***) en regard des noms de partition pour chacune des partitions que vous venez de créer. Cela indique que la partition n'a pas été traitée (actualisée). Lorsque vous créez de nouvelles partitions, vous devez exécuter une opération « Traiter les partitions » ou « Traiter la table » pour actualiser les données dans ces partitions.  
  
#### Pour traiter les partitions Internet Sales  
  
1.  Cliquez sur **OK** pour fermer la boîte de dialogue **Gestionnaire de partition**.  
  
2.  Dans le Concepteur de modèles, cliquez sur la table **Internet Sales**, cliquez sur le menu **Modèle**, puis pointez sur **Traiter** (Actualiser) et enfin, cliquez sur **Traiter les partitions**.  
  
3.  Dans la boîte de dialogue **Traiter les partitions**, vérifiez que le **Mode** est défini sur **Traiter par défaut**.  
  
4.  Cochez la case dans la colonne **Traiter** pour chacune des cinq partitions que vous avez créées, puis cliquez sur **OK**.  
  
    Si vous êtes invité à fournir les informations d'emprunt d'identité, entrez le nom d'utilisateur Windows et le mot de passe spécifiés dans la leçon 2, étape 6.  
  
    La boîte de dialogue **Traitement des données** apparaît et affiche les détails du traitement pour chaque partition. Notez qu'un nombre de lignes différent est transféré pour chaque partition. Cela est dû au fait que chaque partition contient uniquement les lignes de l'année spécifiée dans la clause WHERE dans l'instruction SQL. Quand le traitement est terminé, continuez et fermez la boîte de dialogue Traitement des données.  
  
  
  
## Étapes suivantes  
Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 12 : Créer des rôles](../analysis-services/lesson-12-create-roles.md).  
  
  
  
