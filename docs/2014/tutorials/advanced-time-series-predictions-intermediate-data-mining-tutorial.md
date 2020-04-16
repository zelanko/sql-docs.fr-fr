---
title: Prévisions de séries chronologiques avancées (Intermediate Data Mining Tutorial) Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ca144d1d473f7df49f73d5ed170052c61ce6107d
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "68893688"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a>Prédictions de série chronologique avancées (Didacticiel intermédiaire sur l'exploration de données)
  Le modèle de prévision vous a appris que même si les ventes dans la plupart des régions suivent une tendance similaire, certaines régions et certains modèles, tels que le modèle M200 dans la région Pacific, présentent des tendances très différentes. Ceci n'est pas une surprise puisque vous savez que les différences entre les régions sont courantes et sont causées par de nombreux facteurs, notamment les promotions marketing, la création de rapports inexacts ou des événements géopolitiques.  
  
 Toutefois, vos utilisateurs demandent un modèle qui peut être appliqué dans le monde entier. C'est pourquoi, dans le but de réduire la portée de facteurs individuels sur les projections, vous décidez de générer un modèle basé sur les mesures cumulées des ventes internationales. Vous pouvez alors utiliser ce modèle pour faire des prédictions pour chacune des régions.  
  
 Dans cette tâche, vous allez générer toutes les sources de données dont vous avez besoin pour effectuer les tâches de prédiction avancées. Vous allez créer deux vues de source de données à utiliser comme entrées à la requête de prédiction, et une vue de source de données à utiliser lors de la génération d'un nouveau modèle.  
  
 **Étapes**  
  
1.  [Préparez les données de ventes étendues (pour la prédiction)](#bkmk_newExtendData)  
  
2.  [Préparez les données cumulées (pour générer le modèle)](#bkmk_newReplaceData)  
  
3.  [Préparez les données de la série (pour la prédiction croisée)](#bkmk_CrossData2)  
  
4.  [Effectuez les prédictions à l'aide d'EXTEND](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [Créez le modèle de prédiction croisée](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [Effectuez les prédictions à l'aide de REPLACE](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [Examinez les nouvelles prédictions](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="creating-the-new-extended-sales-data"></a><a name="bkmk_newExtendData"></a>Création des nouvelles données sur les ventes étendues  
 Pour mettre à jour vos données de ventes, vous devez obtenir les derniers chiffres de vente. Les données qui viennent d'arriver de la région Pacific sont d'un intérêt particulier car cette région a lancé une promotion commerciale régionale pour attirer l'attention sur les nouveaux magasins et pour attiser la conscience de leurs produits.  
  
 Pour ce scénario, nous supposerons que les données ont été importées à partir d’un manuel Excel qui ne contient que trois mois de nouvelles données pour quelques régions. Vous créerez une table pour les données à l’aide d’un script Transact-SQL, puis définirez une vue source de données à utiliser pour la prédiction.  
  
#### <a name="create-the-table-with-new-sales-data"></a>Créez la table avec les nouvelles données de ventes  
  
1.  Dans une fenêtre de requête Transact-SQL, exécutez l'instruction suivante pour ajouter les données de ventes à la base de données AdventureWorksDW (ou une autre base de données).  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  Insérez les nouvelles valeurs à l'aide du script suivant.  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  Les guillemets sont utilisés avec les valeurs monétaires pour empêcher les problèmes liés au séparateur à virgule et au symbole monétaire. Vous pouvez également transmettre les valeurs monétaires dans ce format : `130170.22`  
    >   
    >  Notez que les dates utilisées dans l'exemple de base de données ont changé pour cette version. Si vous utilisez une version antérieure d'AdventureWorks, vous devrez peut-être ajuster les dates insérées en conséquence.  
  
###  <a name="create-a-data-source-view-using-the-new-sales-data"></a><a name="bkmk_newReplaceData"></a>Créer une vue source de données à l’aide des nouvelles données de vente  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur **Vues des sources de données**, puis sélectionnez **Nouvelle vue de source de données**.  
  
2.  Dans l'Assistant Vue de source de données, faites les sélections suivantes :  
  
     **Source de données**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **Sélectionnez Tables et Vues**: Sélectionnez la table que vous venez de créer, NewSalesData.  
  
3.  Cliquez sur **Terminer**.  
  
4.  Dans la surface de conception Data Source View, cliquez à droite sur NewSalesData, puis sélectionnez **Explorez les données** pour vérifier les données.  
  
> [!WARNING]  
>  Vous allez utiliser ces données uniquement pour la prédiction, donc il n'est pas important que ces données soient incomplètes.  
  
##  <a name="creating-the-data-for-the-cross-prediction-model"></a><a name="bkmk_CrossData2"></a>Création des données pour le modèle de prédation croisée  
 Les données utilisées dans le modèle de prévision d'origine ont déjà été groupées, dans une certaine mesure, par la vue vTimeSeries qui a réduit plusieurs modèles de vélos en un plus petit nombre de catégories et fusionné les résultats de différents pays en régions. Pour créer un modèle qui peut être utilisé pour les projections internationales, vous allez créer des agrégations simples supplémentaires directement dans le Concepteur de vue de source de données. La nouvelle vue de source de données ne contiendra qu'une somme et une moyenne des ventes de tous les produits pour toutes les régions.  
  
 Après avoir créé la source de données utilisée pour le modèle, vous devez créer une nouvelle vue de source de données pour la prédiction. Par exemple, si vous souhaitez prédire des ventes pour l'Europe à l'aide du nouveau modèle international, vous devez charger uniquement les données de la région Europe. Vous allez définir une nouvelle vue de source de données qui filtre les données d'origine et modifier la condition de filtre pour chaque ensemble de requêtes de prédiction.  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a>Pour créer les données de modèle à l'aide d'une vue de source de données personnalisée  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur **Vues des sources de données**, puis sélectionnez **Nouvelle vue de source de données**.  
  
2.  Dans la page d'accueil de l'Assistant, cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner une source de données** , sélectionnez [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], puis cliquez sur **Suivant**.  
  
4.  Dans la page, **Sélectionnez les tables et les vues**, n’ajoutez pas de tables-il juste cliquez sur **Suivant**.  
  
5.  Sur la page, **Compléter le** `AllRegions`Magicien , tapez le nom , puis cliquez sur **Finition**.  
  
6.  Ensuite, cliquez avec le bouton droit sur l'aire de conception Vue de source de données vierge, puis sélectionnez **Nouvelle requête nommée**.  
  
7.  Dans la boîte de dialogue De requête `AllRegions`nommée **créer,** pour le **nom**, le type , et pour la **description**, la somme de type et la moyenne des ventes pour tous les modèles **et régions**.  
  
8.  Dans le volet Texte SQL, tapez l'instruction suivante et cliquez sur OK :  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. Cliquez à `AllRegions` droite sur la table, puis sélectionnez **Explorez les données**.  
  
###  <a name="to-create-the-series-data-for-cross-prediction"></a><a name="bkmk_CrossData"></a>Créer les données de la série pour la ressurée  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur **Vues des sources de données**, puis sélectionnez **Nouvelle vue de source de données**.  
  
2.  Dans l'Assistant Vue de source de données, faites les sélections suivantes :  
  
     **Source de données**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **Sélectionner des tables et des vues**: ne sélectionnez pas de tables  
  
     **Nom**:`T1000 Pacific Region`  
  
3.  Cliquez sur **Terminer**.  
  
4.  Cliquez avec le bouton droit sur l'aire de conception vide pour **1000 Pacific Region.dsv**, puis sélectionnez **Nouvelle requête nommée**.  
  
     La boîte de dialogue **Créer une requête nommée** s'affiche. Retapez le nom, puis ajoutez la description suivante :  
  
     **Nom**:`T1000 Pacific Region`  
  
     **Description**: **Filtre`vTimeSeries`par région et modèle**  
  
5.  Dans le volet Texte, tapez la requête suivante et cliquez sur OK :  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  Puisque vous devez créer des prédictions séparément pour chaque série, vous pouvez copier le texte de la requête et l'enregistrer dans un fichier texte afin de le réutiliser pour les autres séries de données.  
  
6.  Dans la surface de conception Data Source View, cliquez à droite sur T1000 Pacific, puis sélectionnez **Explorez les données** pour vérifier que les données sont filtrées correctement.  
  
     Vous utiliserez ces données comme entrée au modèle lors de la création des requêtes de prédiction croisée.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Prévisions de séries chronologiques à l’aide de données mises à jour &#40;tutoriel intermédiaire d’exploration de données&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme microsoft série temporelle](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Microsoft Time Series Algorithme Référence technique](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Vues de sources de données dans les modèles multidimensionnels](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
