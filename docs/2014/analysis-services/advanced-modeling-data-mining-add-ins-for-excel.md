---
title: Modélisation avancée (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 669fa1fcd9e4802a4d4102120a373dd615741017
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062737"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>Modélisation avancée (Compléments d'exploration de données pour Excel)
  Vous pouvez utiliser les options de modélisation **avancée** des données pour créer des modèles et des structures d’exploration de données personnalisés avec des paramètres différents de ceux créés par les assistants. Les deux Assistants décrits de cette section vous aident à créer une nouvelle structure d'exploration de données et un nouveau modèle d'exploration de données à appliquer à une structure d'exploration de données existante.  
  
## <a name="create-mining-structure"></a>Créer une structure d’exploration de données  
 ![Bouton Créer une structure d'exploration de données, ruban Exploration de données](media/dmc-createstruct.gif "Bouton Créer une structure d'exploration de données, ruban Exploration de données")  
  
 L' **Assistant Création** d’une structure d’exploration de données vous aide à générer une nouvelle structure d’exploration de données. Une structure désigne un ensemble de données extraites depuis une source de données spécifiée.  Une structure d'exploration de données peut être mise à jour avec de nouvelles données à la source, mais lorsque vous créez la structure d'exploration de données, vous définissez les types de données et les noms qui déterminent la façon dont les données sont utilisées pour l'analyse.  
  
 Vous pouvez utiliser les sources de données suivantes pour concevoir votre structure : un tableau Excel, une plage Excel, ou toutes les données d'une source de données externe qui a déjà été définie comme vue de source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour chaque structure, vous pouvez mettre de côté certaines données à utiliser pour le test et la validation. En créant ce *jeu de données exclusion* lorsque vous configurez vos sources de données, vous pouvez vous assurer que tous les modèles basés sur la structure sont en mesure d’utiliser un jeu de données cohérent à des fins de test.  
  
 Après avoir créé une structure d'exploration de données, vous pouvez ajouter plusieurs modèles pour appliquer différentes méthodes d'analyse.  
  
 Pour plus d’informations sur l’utilisation de l' **Assistant Création**d’une structure d’exploration de données, consultez [créer une structure d’exploration de données &#40;SQL Server des compléments d’exploration de données&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).  
  
## <a name="add-model-to-structure"></a>Ajouter un modèle à une structure  
 ![Bouton Ajouter le modèle à la structure](media/dmc-addmodel.gif "Bouton Ajouter le modèle à la structure")  
  
 Lorsque vous ajoutez un nouveau modèle à une structure, vous analysez les données à l'aide d'un autre algorithme ou avec d'autres paramètres. Cette option est notamment utile si vous souhaitez créer un modèle à l'aide d'un des algorithmes non exposés dans les outils du client d'exploration de données.  
  
 Par exemple, vous pouvez utiliser les algorithmes pris en charge par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], tels que :  
  
-   Régression linéaire  
  
-   Sequence clustering  
  
-   Analyse d'association sur les jeux de données imbriqués  
  
 Pour voir quels types de structures d’exploration de données sont disponibles, vous pouvez parcourir les modèles et [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] les structures stockés dans en cliquant sur **gérer les modèles** ou sur **Parcourir**.  
  
 Vous êtes limité aux structures d'exploration de données qui ont été créées pendant la session active, ou aux structures d'exploration de données qui ont été enregistrées dans une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour plus d’informations, consultez [Ajouter un modèle à une Structure &#40;compléments d’exploration de données pour Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les modèles &#40;SQL Server des compléments d’exploration de données&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [Exploration des modèles dans Excel &#40;SQL Server les compléments d’exploration de données&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
