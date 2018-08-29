---
title: 'Leçon du didacticiel Analysis Services 10 : créer des partitions | Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: b7a4cfcb32023c20e05728a3faac3715278c1019
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43091327"
---
# <a name="create-partitions"></a>Créer des partitions

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez des partitions pour diviser la table FactInternetSales en sous-parties logiques qui peuvent être traitées (actualisées) indépendamment d’autres partitions. Par défaut, chaque table que vous incluez dans votre modèle comporte une partition, ce qui inclut les colonnes et lignes de toutes les table. Pour la table FactInternetSales, nous souhaitons diviser les données par année ; une seule partition pour chacune des cinq années de la table. Chaque partition peut ensuite être traitée indépendamment. Pour plus d’informations, consultez [Partitions](../tabular-models/partitions-ssas-tabular.md). 
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [leçon 9 : créer des hiérarchies](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Créer des partitions  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Pour créer des partitions dans la table FactInternetSales  
  
1.  Dans l’Explorateur de modèles tabulaires, développez **Tables**et avec le bouton droit puis **FactInternetSales** > **Partitions**.  
  
2.  Dans le Gestionnaire de Partition, cliquez sur **copie**, puis modifiez le nom à **FactInternetSales2010**.
  
    Étant donné que vous souhaitez que la partition inclue uniquement les lignes d’une période donnée, pour l’année 2010, vous devez modifier l’expression de requête.
  
4.  Cliquez sur **conception** pour ouvrir l’éditeur de requête, puis cliquez sur le **FactInternetSales2010** requête.

5.  Dans l’aperçu, cliquez sur la flèche bas dans la **OrderDate** en-tête de colonne, puis cliquez sur **filtres de Date/heure** > **entre**.

    ![en tant que-lesson10--éditeur de requête](../tutorial-tabular-1400/media/as-lesson10-query-editor.png)

6.  Dans la boîte de dialogue Filtrer les lignes dans **afficher les lignes où : OrderDate**, laissez **est postérieur ou égal à**, puis dans le champ de date, entrez **1/1/2010**. Laissez le **et** opérateur sélectionné, puis sélectionnez **est avant**, puis dans le champ de date, entrez **1/1/2011**, puis cliquez sur **OK**.

    ![en tant que-lesson10-filtre-rows](../tutorial-tabular-1400/media/as-lesson10-filter-rows.png)
    
    Notez que dans l’éditeur de requête, dans la section étapes appliquées, vous consultez une autre étape nommée lignes filtrées. Ce filtre consiste à sélectionner uniquement les dates de commande à partir de 2010.

8.  Cliquez sur **Importer**.

    Dans le Gestionnaire de Partition, notez que maintenant l’expression de requête a une clause lignes filtrées supplémentaire.

    ![en tant que requête de lesson10](../tutorial-tabular-1400/media/as-lesson10-query.png)
  
    Cette instruction spécifie que cette partition doit inclure uniquement les données dans les lignes où OrderDate correspond à l’année 2010, comme spécifié dans la clause lignes filtrées.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>Pour créer une partition pour l’année 2011  
  
1.  Dans la liste des partitions, cliquez sur le **FactInternetSales2010** de partition que vous avez créé, puis cliquez sur **copie**.  Remplacez le nom de la partition par **FactInternetSales2011**. 

    Vous n’avez pas besoin d’utiliser l’éditeur de requête pour créer une nouvelle clause lignes filtrées. Étant donné que vous avez créé une copie de la requête pour 2010, il vous suffit est réalisent une légère modification dans la requête pour 2011.
  
2.  Dans **Expression de requête**, dans l’ordre pour cette partition inclue uniquement les lignes pour l’année 2011, remplacez les années dans la clause lignes filtrées avec **2011** et **2012**, respectivement, comme :  
  
    ```  
    let
        Source = #"SQL/localhost;AdventureWorksDW2014",
        dbo_FactInternetSales = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
        #"Removed Columns" = Table.RemoveColumns(dbo_FactInternetSales,{"OrderDateKey", "DueDateKey", "ShipDateKey"}),
        #"Filtered Rows" = Table.SelectRows(#"Removed Columns", each [OrderDate] >= #datetime(2011, 1, 1, 0, 0, 0) and [OrderDate] < #datetime(2012, 1, 1, 0, 0, 0))
    in
        #"Filtered Rows"
   
    ```  
  
#### <a name="to-create-partitions-for-2012-2013-and-2014"></a>Pour créer des partitions pour 2012, 2013 et 2014.  
  
- Suivez les étapes précédentes, la création de partitions pour 2012, 2013 et 2014, en modifiant les années dans la clause lignes filtrées pour inclure uniquement les lignes de cette année. 
  

## <a name="delete-the-factinternetsales-partition"></a>Supprimer la partition FactInternetSales

Maintenant que vous avez des partitions pour chaque année, vous pouvez supprimer la partition FactInternetSales ; éviter un chevauchement lorsque vous choisissez de traiter toutes les lors du traitement des partitions.

#### <a name="to-delete-the-factinternetsales-partition"></a>Pour supprimer la partition FactInternetSales

-  Cliquez sur le **FactInternetSales** de partition, puis cliquez sur **supprimer**.



## <a name="process-partitions"></a>Traiter les partitions  

Dans le Gestionnaire de Partition, notez que le **dernier traitement** colonne pour chacune des partitions créées montre ces partitions n’ont jamais été traitées. Lorsque vous créez des partitions, vous devez exécuter une opération de traiter les Partitions ou traiter la Table pour actualiser les données dans ces partitions.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>Pour traiter les partitions FactInternetSales  
  
1.  Cliquez sur **OK** pour fermer le Gestionnaire de Partition.  
  
2.  Cliquez sur le **FactInternetSales** table, puis cliquez sur le **modèle** menu > **processus** > **traiter les Partitions**.  
  
3.  Dans la boîte de dialogue traiter les Partitions, vérifiez **Mode** a la valeur **traiter par défaut**.  
  
4.  Cochez la case dans la colonne **Traiter** pour chacune des cinq partitions que vous avez créées, puis cliquez sur **OK**.  

    ![en tant que-lesson10-processus-partitions](../tutorial-tabular-1400/media/as-lesson10-process-partitions.png)
  
    Si vous êtes invité à entrer les informations d’identification de l’emprunt d’identité, entrez le nom d’utilisateur Windows et le mot de passe spécifiés dans la leçon 2.  
  
    La boîte de dialogue **Traitement des données** apparaît et affiche les détails du traitement pour chaque partition. Notez qu'un nombre de lignes différent est transféré pour chaque partition. Chaque partition contient uniquement les lignes de l’année spécifiée dans la clause WHERE dans l’instruction SQL. Quand le traitement est terminé, continuez et fermez la boîte de dialogue Traitement des données.  
  
    ![en tant que-lesson10-processus-complete](../tutorial-tabular-1400/media/as-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Quelle est l’étape suivante ?

Accédez à la leçon suivante : [leçon 11 : créer des rôles](../tutorial-tabular-1400/as-lesson-11-create-roles.md). 
