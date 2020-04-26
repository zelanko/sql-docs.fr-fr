---
title: Ajout d’une vue de source de données pour la prévision (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f60ea2b2a642cf9435ed8366c42e43abb927e426
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62823129"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>Ajout d'une vue de source de données à des fins de prévision (Didacticiel sur l'exploration de données intermédiaire)
  Au cours de cette tâche, vous allez ajouter une vue de source de données qui sera utilisée pour le scénario de prévision. Un modèle de prévision requiert que les données contiennent une colonne pouvant être utilisée pour identifier des étapes dans une série chronologique. Si vous envisagez d'analyser plusieurs séries de données, toutes les séries doivent se terminer à la même date ou heure.  
  
### <a name="to-add-a-data-source-view"></a>Pour ajouter une vue de source de données  
  
1.  Dans Explorateur de solutions, cliquez avec le bouton droit sur **vues de source de données**, puis sélectionnez **nouvelle vue de source de données**.  
  
2.  Sur la page **Bienvenue dans l'Assistant Sources de données**, cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner une source de données** , sous **sources de données relationnelles**, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sélectionnez la source de données. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous ne disposez pas de cette source de données, vous trouverez les étapes nécessaires à la création de la source de données dans le didacticiel sur l' [exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
4.  Sur la page **Sélectionner des tables et des vues** , sélectionnez la table vTimeSeries (DBO), puis cliquez sur la flèche droite pour l’ajouter à la vue de source de données.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **fin de l’Assistant** , la vue de source de données est [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]nommée par défaut. Remplacez le nom par **SalesByRegion**, puis cliquez sur **Terminer**.  
  
     Le concepteur de vue de source de données s’ouvre et la vue de source de données **SalesByRegion** s’affiche.  
  
## <a name="working-with-the-data-source-view"></a>Utilisation de la vue de source de données  
 Une fois que vous avez créé la vue de source de données, pour explorer les données, vous pouvez procéder des manières suivantes :  
  
-   Cliquez avec le bouton droit sur la table vTimeSeries dans le concepteur, puis sélectionnez **Explorer les données** pour ouvrir la table sélectionnée dans une grille.  
  
-   Cliquez sur **options d’échantillonnage** , puis utilisez la boîte de dialogue Options d’exploration de **données** pour modifier la méthode d’échantillonnage. Cliquez sur **Actualiser** pour charger les données dans la table à l’aide des nouveaux paramètres d’option. Par exemple, vous pouvez spécifier le nombre de lignes à générer dans l’exemple ou choisir les n premières lignes.  
  
-   Cliquez avec le bouton droit sur la table vTimeSeries, puis sélectionnez **Propriétés** pour affecter un nouveau nom à la table. Vous pouvez également sélectionner des colonnes individuelles dans la vue de source de données et modifier les propriétés des colonnes.  
  
-   Cliquez n'importe où dans la zone de conception de la vue de source de données pour créer une nouvelle requête et lui affecter un nom, pour créer des relations entre des tables, ou pour modifier la disposition de la zone de conception.  
  
-   Cliquez avec le bouton droit sur une table et sélectionnez **nouveau calcul nommé** pour créer des colonnes dérivées, y compris les agrégations. Vous pouvez également ajouter de nouvelles tables et des vues à partir de la source de données dans cette vue.  
  
 Dans la tâche suivante, vous allez explorer les données de série chronologique et déterminer la meilleure colonne à utiliser comme identificateur de série chronologique. Vous allez également apprendre à gérer les écarts dans les données de série chronologique.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Comprendre la configuration requise pour un modèle de série chronologique &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
