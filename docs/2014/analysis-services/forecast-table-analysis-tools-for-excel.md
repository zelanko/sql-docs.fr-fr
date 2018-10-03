---
title: Prévisions (outils d’analyse de Table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b60e17ca95bff865d1a0786aa7da5ee398adcb7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170290"
---
# <a name="forecast-table-analysis-tools-for-excel"></a>Prévisions (Outils d'analyse de table pour Excel)
  ![Ruban des outils de prévision de bouton dans l’analyse de Table](media/tat-forecast.gif "bouton prévisions dans le ruban des outils d’analyse de Table")  
  
 Le **prévision** outil vous permet de faire des prédictions basées sur les données dans une table de données Excel ou une autre source de données et également de consulter les probabilités associées à chaque valeur prédite. Par exemple, si vos données contiennent une colonne de date et une colonne qui affiche le total des ventes pour chaque jour du mois, vous pouvez prévoir les ventes des jours à venir. Vous pouvez également spécifier le nombre de prédictions à faire. Par exemple, vous pouvez prévoir cinq ou trente jours.  
  
 Une fois l'outil terminé, celui-ci ajoute les nouvelles prédictions à la fin du tableau de données sources et met en évidence les nouvelles valeurs. Les nouvelles valeurs de série chronologique ne sont pas ajoutées ; vous pouvez ainsi examiner d'abord les prédictions.  
  
 L’outil crée également une nouvelle feuille de calcul nommée **rapport des prévisions**. Cette feuille de calcul indique si l'Assistant a réussi a créer ou non une prédiction. La nouvelle feuille de calcul contient aussi un graphique linéaire qui présente les tendances historiques.  
  
 Lorsque vous étendez la série chronologique pour inclure les nouvelles prédictions, les valeurs prédites sont ajoutées au graphique linéaire. Les valeurs historiques sont représentées sous la forme d'un trait continu et les prédictions sont en pointillés.  
  
## <a name="using-the-forecast-tool"></a>Utilisation de l'outil Prévision  
  
1.  Ouvrez un tableau Excel qui contient des données numériques prévisibles.  
  
2.  Cliquez sur **prévision** sur le **analyser** onglet.  
  
3.  Spécifiez les colonnes à prévoir. L'outil sélectionne automatiquement les colonnes dont le type de données est prévisible, c'est-à-dire celles qui contiennent des données numériques continues. L'outil ne peut pas sélectionner certaines colonnes qui contiennent des données numériques continues si ces colonnes contiennent de nombreuses valeurs null ou égales à zéro, car les données manquantes peuvent affecter les résultats. Si cela se produit, vous pouvez corriger les données à l’aide de la [Réétiqueter &#40;SQL Server Data Mining Add-ins&#41; ](relabel-sql-server-data-mining-add-ins.md) outil.  
  
4.  Spécifiez la colonne qui contient la date, l'heure ou un autre identificateur pour la série. Si vous sélectionnez l’option  **\<aucun horodatage >** l’outil créera une série selon l’ordre des lignes dans la source de données.  
  
5.  Spécifiez le nombre de prédictions à faire.  
  
6.  Vous pouvez également fournir un indicateur à l'algorithme sur la fréquence de vos données, hebdomadaires, mensuelles ou autres fréquences. Si vos données ne répondent pas aux modèles spécifiés, ou si vous ne savez pas de modèles, sélectionnez  **\<détecter automatiquement >** pour que l’outil recherche les périodes de temps extensible.  
  
7.  L'Assistant ajoute les prédictions au tableau source et crée un rapport de prévisions dans une nouvelle feuille de calcul.  
  
8.  Pour ajouter les nouvelles valeur au graphique de prédiction, étendez la série chronologique pour inclure les valeurs projetées.  
  
### <a name="requirements"></a>Spécifications  
 Les colonnes que vous prévoyez doivent contenir des données numériques continues (devise ou autres nombres).  
  
 Si possible, vos données doivent également inclure une colonne qui contient une série de dates ou d'heures. Vous pouvez utiliser une série numérique (1,2,3...) à la place des données de date et d'heure. Cependant, les valeurs dans la colonne de série doivent être uniques. Une erreur se produit si le **prévision** outil recherche les valeurs en double dans la colonne de la série.  
  
 Vous ne pouvez pas prévoir une date à l’aide de la **prévision** outil. Même en l'absence d'erreur, cet algorithme n'est pas conçu pour utiliser des dates comme des valeurs prévisibles.  
  
### <a name="understanding-time-stamps"></a>Fonctionnement des horodatages  
 Vous devez identifier une colonne à utiliser comme un *horodatage*. L'horodatage a deux fonctions. En premier lieu, il identifie de façon unique une valeur dans une série chronologique. Par exemple, si vous suivez les ventes tous les jours, vous ne devez avoir qu'une seule valeur des ventes pour chaque jour. La date de calendrier peut être utilisée comme horodatage. En second lieu, la colonne d'horodatage indique l'unité pour faire des prédictions. Si vous suivez les ventes quotidiennes, vos prédictions auront également comme unités des jours.  
  
 Si vos données ne contiennent pas une colonne de date ou une colonne d'heure, l'outil créera automatiquement une clé de série temporaire, appelée _RowIndex. Cette clé sera basée sur l'ordre des lignes dans le jeu de données.  
  
 Lorsque vous spécifiez le nombre de prédictions, vous entrez un nombre entier qui indique le nombre d'étapes. Les unités utilisées pour ces étapes dépendent des unités utilisées dans la série chronologique de vos données. Si vos données répertorient les résultats des ventes par mois, la prédiction sera établie pour une série de mois. Vous ne pouvez pas modifier les unités d'heure à moins de modifier les données sources.  
  
### <a name="understanding-periodicity"></a>Fonctionnement de la périodicité  
 Une prévision est basée sur des séquences qui se répètent sur un laps de temps. Par conséquent, l'algorithme MTS (Microsoft Time Series) effectue des calculs pour déterminer les périodes de temps qui ont les séquences les plus fortes. *Périodicité* fait référence à ces périodes de temps.  
  
 Une série chronologique peut contenir de nombreuses séquences potentielles. Si vous êtes certain que vos données contiennent une certaine séquence, vous pouvez améliorer la qualité de prédiction en fournissant une indication à l'algorithme.  
  
 Par exemple, si vous pensez que vos données se répètent de façon hebdomadaire, vous pouvez sélectionner Hebdomadaire pour indiquer que l'algorithme doit rechercher des séquences hebdomadaires. Cependant, si aucune séquence hebdomadaire forte n'est trouvée, l'algorithme ignorera l'indication.  
  
## <a name="understanding-the-forecasting-report"></a>Rapport des prévisions  
 Dans ce graphique, les valeurs historiques issues de votre table de données sont représentées sous la forme d'un trait noir. Les valeurs prédites apparaissent comme traits pointillés. Vous pouvez cliquer sur un point de la ligne pour consulter la valeur prédite.  
  
> [!NOTE]  
>  Si vous ne voyez pas les étiquettes sur l’axe temporel pour les valeurs prédites dans le graphique, ouvrez la feuille de calcul qui contient les valeurs prédites et utilisez le **remplissage, séries** dans Excel pour étendre la colonne d’horodatage pour inclure le prédite (fonction) valeurs.  
  
 Dans certains cas, la prévision peut ne pas contenir autant de tranches de temps que prévu. Cela signifie habituellement que les données sont insuffisantes pour permettre à l'algorithme de prévoir aussi loin dans l'avenir. Le **prévision** outil n’effectue que des prédictions qui répondent à un seuil de probabilité minimal.  
  
## <a name="related-tools"></a>Outils connexes  
 Le Client d'exploration de données pour Excel, complément séparé qui fournit d'autres fonctionnalités d'exploration de données plus avancées, contient aussi un Assistant pour la prévision.  
  
 Les deux le **prévision** outil (dans les outils d’analyse de Table pour Excel) et le **prévision** utilisation de l’Assistant (dans le Client d’exploration de données pour Excel) le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de série chronologique.  
  
-   Le **prévision** outil est plus facile à utiliser, car il configure automatiquement l’algorithme pour utiliser les paramètres qui conviennent le mieux à vos données.  
  
-   Le **prévision** Assistant dans le Client d’exploration de données pour Excel vous offre la possibilité de personnaliser les paramètres.  
  
 Pour plus d’informations sur la **prévision** Assistant, consultez [Assistant prévision &#40;des compléments d’exploration de données pour Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md). Pour plus d'informations sur l'algorithme utilisé pour la prévision, consultez la rubrique « Algorithme MTS (Microsoft Time Series) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d’analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  
