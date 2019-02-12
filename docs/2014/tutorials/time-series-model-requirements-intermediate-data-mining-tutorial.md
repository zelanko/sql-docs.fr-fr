---
title: Présentation de la configuration requise pour une série chronologique de modèle (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1ce2b3e3-108a-4f7e-985f-a20b816d0da7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5b3438e832f28329cb0fec764d3a4846bae18ede
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035150"
---
# <a name="understanding-the-requirements-for-a-time-series-model-intermediate-data-mining-tutorial"></a>Spécifications pour un modèle de série chronologique (Didacticiel sur l'exploration de données intermédiaire)
  Lorsque vous préparez des données afin de les utiliser dans un modèle de prévision, vous devez veiller à ce qu'elles contiennent une colonne pouvant être utilisée pour identifier les étapes dans la série chronologique. Cette colonne sera désignée comme colonne `Key Time`. Puisqu'il s'agit d'une clé, la colonne doit contenir des valeurs numériques uniques.  
  
 Le choix de la bonne unité pour la colonne `Key Time` est une partie importante de l'analyse. Par exemple, supposons que vos données de ventes soient actualisées minute par minute. Vous n'êtes pas obligé de prendre les minutes comme unité pour la série chronologique ; il peut être plus explicite de regrouper les chiffres des ventes par jour, semaine ou même par mois. Si vous ne savez pas quelle unité de temps utiliser, vous pouvez créer une vue de source de données pour chaque agrégation et générer les modèles associés, pour savoir si différentes tendances émergent à chaque niveau d'agrégation.  
  
 Pour ce didacticiel, les données de ventes sont collectées quotidiennement dans la base de données des ventes transactionnelles, mais pour l'exploration de données, les données ont été préagrégées par mois, à l'aide d'une vue.  
  
 De plus, il est souhaitable pour l'analyse que les données aient aussi peu d'écart possible. Si vous envisagez d'analyser plusieurs séries de données, toutes les séries devraient commencer et se terminer de préférence aux mêmes dates. Si les données ont des écarts, mais les écarts ne sont pas au début ou à la fin d’une série, vous pouvez utiliser le paramètre MISSING_VALUE_SUBSTITUTION pour remplir la série. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit également plusieurs options permettant de remplacer des données manquantes par des données, telles que l'utilisation de moyennes ou de constantes.  
  
> [!WARNING]  
>  Les outils de graphique croisé dynamique et de tableau croisé dynamique qui ont été inclus dans les versions antérieures du concepteur de vue de source de données ne sont plus fournis. Nous vous conseillons d'identifier au préalable les écarts dans les données de série chronologique à l'aide des outils tels que le profileur de données inclus dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
### <a name="to-identify-the-time-key-for-the-forecasting-model"></a>Pour identifier la clé de temps pour le modèle de prévision  
  
1.  Dans le volet, **SalesByRegion.dsv [Design]**, avec le bouton droit de la table vTimeSeries, puis sélectionnez **Explorer les données**.  
  
     Un nouvel onglet s’ouvre, intitulé **Explorer la Table vTimeSeries**.  
  
2.  Sur le **Table** onglet, examinez les données qui sont utilisées dans les colonnes TimeIndex et Reportingdate.  
  
     Ces deux sont des séquences comportant des valeurs uniques et peuvent être toutes deux utilisées comme clé de série chronologique ; toutefois, les types de données des colonnes sont différents. L'algorithme MTS (Microsoft Time Series) ne requiert pas de type de données `datetime`, mais uniquement que les valeurs soient distinctes et classées. Par conséquent, l'une ou l'autre des colonnes peuvent être utilisées comme clé de temps pour le modèle de prévision.  
  
3.  Dans l’aire de conception vue de source de données, sélectionnez la colonne, la Date de création de rapports, puis sélectionnez **propriétés**. Ensuite, cliquez sur la colonne TimeIndex et sélectionnez **propriétés**.  
  
     Le champ TimeIndex a les type de données System.Int32, tandis que le champ Date de création d’un rapport au type de données System.DateTime. De nombreux entrepôts de données convertissent les valeurs date/heure en entiers et utilisent la colonne des entiers comme clé pour améliorer les performances d'indexation. Toutefois, si vous utilisez cette colonne, l'algorithme MTS établit des prédictions à l'aide de valeurs futures, telles que 201014, 201014, etc. Étant donné que vous souhaitez représenter vos données de ventes de prévision à l’aide de dates de calendrier, vous allez utiliser la colonne Reportingdate comme identificateur de série unique.  
  
### <a name="to-set-the-key-in-the-data-source-view"></a>Pour définir la clé dans la vue de source de données  
  
1.  Dans le volet **SalesByRegion.dsv**, sélectionnez la table vTimeSeries.  
  
2.  Avec le bouton droit de la colonne, la Date de création de rapports, puis sélectionnez **définir la clé primaire logique**.  
  
## <a name="handling-missing-data-optional"></a>Gestion des données manquantes (facultatif)  
 S'il manque des données dans une série, vous risquez d'obtenir une erreur lorsque vous essayez de traiter le modèle. Il existe plusieurs manières de gérer les données manquantes :  
  
-   Vous pouvez laisser Analysis Services remplir les valeurs manquantes, en calculant une moyenne ou en utilisant une valeur précédente. Pour ce faire, définissez le paramètre MISSING_VALUE_SUBSTITUTION sur le modèle d'exploration de données. Pour plus d’informations sur ce paramètre, consultez [Microsoft Time Series algorithme Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md). Pour plus d’informations sur la modification des paramètres sur un modèle d’exploration de données existant, consultez [afficher ou modifier les paramètres d’algorithme](../../2014/analysis-services/data-mining/view-or-change-algorithm-parameters.md).  
  
-   Vous pouvez modifier la source de données ou filtrer la vue sous-jacente pour éliminer la série irrégulière ou remplacer des valeurs. Pour ce faire, vous devez utiliser la source de données relationnelle ou modifier la vue de source de données en créant des requêtes ou des calculs nommés personnalisés. Pour plus d’informations, consultez [Vues de sources de données dans les modèles multidimensionnels](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md). Une tâche ultérieure au cours de cette leçon fournit un exemple de la manière de générer à la fois une requête nommée et un calcul personnalisé.  
  
 Pour ce scénario, certaines données manquent au début d'une série : autrement dit, il n'y a pas de données pour la gamme de produits T1000 jusqu'en juillet 2007. Sinon, toutes les séries se terminent à la même date et aucune valeur ne manque.  
  
 La configuration requise de l’algorithme Microsoft Time Series est que toute série que vous incluez dans un modèle unique doit avoir le même **fin** point. Étant donné que le modèle de vélo T1000 a été introduit en 2007, les données de cette série démarrent plus tard que pour les autres modèles de vélos, mais la série se termine à la même date ; les données peuvent donc être utilisées.  
  
#### <a name="to-close-the-data-source-view-designer"></a>Pour fermer le concepteur de vues de source de données  
  
-   Cliquez sur l’onglet, **Explorer la Table vTimeSeries**, puis sélectionnez **fermer**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une Structure de prévision et un modèle &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
