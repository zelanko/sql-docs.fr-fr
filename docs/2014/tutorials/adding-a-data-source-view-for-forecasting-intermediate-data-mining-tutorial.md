---
title: Ajout d’une données vue de Source pour la prévision (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
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
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034800"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>Ajout d'une vue de source de données à des fins de prévision (Didacticiel sur l'exploration de données intermédiaire)
  Au cours de cette tâche, vous allez ajouter une vue de source de données qui sera utilisée pour le scénario de prévision. Un modèle de prévision requiert que les données contiennent une colonne pouvant être utilisée pour identifier des étapes dans une série chronologique. Si vous envisagez d'analyser plusieurs séries de données, toutes les séries doivent se terminer à la même date ou heure.  
  
### <a name="to-add-a-data-source-view"></a>Pour ajouter une vue de source de données  
  
1.  Dans l’Explorateur de solutions, cliquez sur **les vues de sources de données**, puis sélectionnez **nouvelle vue de Source de données**.  
  
2.  Dans la page **Assistant Vue de source de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner une Source de données** page sous **sources de données relationnelles**, sélectionnez le [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] source de données. Cliquer sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous n’avez pas de cette source de données, vous trouverez les étapes pour créer la source de données dans le [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
4.  Sur le **sélectionner des Tables et vues** page, sélectionnez la table vTimeSeries (dbo) et puis cliquez sur la flèche droite pour l’ajouter à la vue de source de données.  
  
5.  Cliquer sur **Suivant**.  
  
6.  Sur le **fin de l’Assistant** page, la vue de source de données est nommée par défaut [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Remplacez le nom par **SalesByRegion**, puis cliquez sur **Terminer**.  
  
     Concepteur de vue de Source de données s’ouvre et la **SalesByRegion** vue de source de données s’affiche.  
  
## <a name="working-with-the-data-source-view"></a>Utilisation de la vue de source de données  
 Une fois que vous avez créé la vue de source de données, pour explorer les données, vous pouvez procéder des manières suivantes :  
  
-   Avec le bouton droit de la table vTimeSeries dans le concepteur, puis sélectionnez **Explorer les données** pour ouvrir la table sélectionnée dans une grille.  
  
-   Cliquez sur **options d’échantillonnage** , puis utilisez le **Options d’Exploration de données** boîte de dialogue pour modifier la méthode d’échantillonnage. Cliquez sur **Actualiser** pour charger des données dans la table en utilisant les nouveaux paramètres d’option. Par exemple, vous pouvez spécifier le nombre de lignes dans l’exemple de sortie, ou choisissez les n premières lignes.  
  
-   Cliquez sur la table vTimeSeries et sélectionnez **propriétés** pour attribuer un nouveau nom à la table. Vous pouvez également sélectionner des colonnes individuelles dans la vue de source de données et modifier les propriétés des colonnes.  
  
-   Cliquez n'importe où dans la zone de conception de la vue de source de données pour créer une nouvelle requête et lui affecter un nom, pour créer des relations entre des tables, ou pour modifier la disposition de la zone de conception.  
  
-   Cliquez sur une table et sélectionnez **nouveau calcul nommé** pour créer des colonnes dérivées, y compris les agrégations. Vous pouvez également ajouter de nouvelles tables et des vues à partir de la source de données dans cette vue.  
  
 Dans la tâche suivante, vous allez explorer les données de série chronologique et déterminer la meilleure colonne à utiliser comme identificateur de série chronologique. Vous allez également apprendre à gérer les écarts dans les données de série chronologique.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Présentation de la configuration requise pour une série chronologique de modèle &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
