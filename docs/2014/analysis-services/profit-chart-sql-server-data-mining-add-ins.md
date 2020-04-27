---
title: Graphique des bénéfices (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- profit chart
- mining models, charting
- mining models, testing
ms.assetid: 5c902543-4da9-4db3-99d5-4ce04c43d7ef
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 32ee1539c734c549f89d5b3db8ec4add467a72b2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070590"
---
# <a name="profit-chart-sql-server-data-mining-add-ins"></a>Graphique des bénéfices (Compléments d'exploration de données SQL Server)
  ![Bouton Graphique des bénéfices sur le ruban Exploration de données](media/dmc-profitchart.gif "Bouton Graphique des bénéfices sur le ruban Exploration de données")  
  
 Un graphique des bénéfices représente l'augmentation de bénéfices estimée qui est associée à l'utilisation d'un modèle d'exploration de données pour déterminer les clients qu'une entreprise doit contacter dans un scénario professionnel. L'axe Y du graphique représente les bénéfices, tandis que l'axe X représente le pourcentage de la population que l'entreprise a contactée. Un graphique des bénéfices classique montre une augmentation des bénéfices jusqu'à un certain point, après lequel les bénéfices diminuent plus le nombre d'individus contactés augmente.  
  
## <a name="configuring-the-profit-chart"></a>Configuration du graphique des bénéfices  
 Si le graphique d'analyse évalue uniquement la probabilité de la validité ou non des prédictions, le graphique des bénéfices intègre des données concrètes sur les conséquences liées à la mise en œuvre d'une prédiction. Cette opération est possible en prenant en compte les facteurs suivants que vous spécifiez lors de l'exécution de l'Assistant :   
  
-   **Habitants**  
  
     Nombre de cas dans le jeu de données qui est utilisé pour créer le graphique de courbes d'élévation. Par exemple, le nombre de clients potentiels.  
  
-   **Coût fixe**  
  
     Coût fixe associé au problème professionnel. En ce qui concerne une solution de publipostage ciblé, le coût ne dépend pas de variables telles que le nombre d'appels téléphoniques effectués ou le nombre de courriers publicitaires de publipostage envoyés.  
  
-   **Coût individuel**  
  
     Coûts s'ajoutant au coût fixe, qui peuvent être associés à chaque client contacté. Par exemple, les courriers publicitaires de publipostage ou les appels téléphoniques.  
  
-   **Revenu par personne**  
  
     Revenu associé à chaque vente réussie.  
  
## <a name="using-the-profit-chart-wizard"></a>Utilisation de l'Assistant Graphique des bénéfices  
 Pour créer un graphique des bénéfices, vous devez référencer un modèle d'exploration de données existant. Vous pouvez parcourir les modèles pour trouver un modèle qui correspond à vos données en cliquant sur **gérer les modèles** ou sur **Parcourir** pour afficher des détails sur l’algorithme utilisé et les colonnes du modèle d’exploration de données.  
  
 Pour plus d’informations, consultez [parcours des modèles dans Excel &#40;SQL Server des compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) et [gérer des modèles &#40;SQL Server compléments d’exploration de données&#41;](manage-models-sql-server-data-mining-add-ins.md).  
  
#### <a name="to-create-a-profit-chart"></a>Pour créer un graphique des bénéfices  
  
1.  Sélectionnez un modèle existant.  
  
2.  Spécifiez la colonne à prévoir et une valeur cible, le cas échéant.  
  
3.  Sélectionnez les données source qui sont les données transmises par le modèle pour créer une prédiction. Vous pouvez ainsi explorer les mêmes données utilisées pour créer le modèle.  
  
4.  Mappez les colonnes dans la nouvelle date (source) aux colonnes utilisées dans le modèle d'exploration de données. Si les noms de colonne sont similaires, l'Assistant les mappe automatiquement.  
  
5.  Entrez les informations de coût requises par l'Assistant : le coût fixe, le coût individuel, le remplissage et le revenu attendu.  
  
6.  Si vous le souhaitez, vous pouvez entrer une série de coûts graduée (cliquez sur le bouton Parcourir **(...)** ). Par exemple, vous pouvez abaisser les coûts d'un publipostage en augmentant le nombre d'éléments envoyés, ce qui vous permet d'entrer un coût différent selon le nombre d'éléments, l'Assistant ajuste automatiquement les coûts pour chaque taille d'échantillon.  
  
7.  L'Assistant crée un graphique qui inclut l'analyse coût-bénéfice du modèle.  
  
### <a name="requirements"></a>Conditions requises  
 Si vous prévoyez une valeur numérique discrète, vous devez sélectionner la valeur cible exacte à prévoir.  
  
## <a name="understanding-the-profit-chart"></a>Fonctionnement du graphique des bénéfices  
 Le graphique des bénéfices contient une ligne verticale grise que vous pouvez déplacer en cliquant à un emplacement dans le graphique. La **légende d’exploration de données** affiche un score, le remplissage correct et la probabilité de prédiction associée à l’emplacement de la ligne grise sur le graphique. Si vous sélectionnez le point des bénéfices maximaux dans le graphique en utilisant la ligne grise, vous pouvez utiliser la valeur de probabilité de prédiction pour déterminer un seuil de probabilité lié au fait de contacter un client.  
  
 Par exemple, si le sommet de la courbe des bénéfices se trouve à 55 % de remplissage et que la probabilité de prédiction associée est de 20 %, cela indique que pour réaliser des bénéfices maximaux, vous devez contacter uniquement les clients dont la réponse est prévue avec une probabilité de 20 % ou plus.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des modèles et utilisation de modèles pour la prédiction &#40;compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
