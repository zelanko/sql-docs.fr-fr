---
title: Requête (SQL Server les compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d0f0212795adcaed220806f8cc1349f95c2a6f3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539571"
---
# <a name="query-sql-server-data-mining-add-ins"></a>Requête (Compléments d'exploration de données SQL Server)
  ![Bouton Modèle de requête, ruban Exploration de données](media/dmc-query.gif "Bouton Modèle de requête, ruban Exploration de données")  
  
 L'Assistant **Requête** vous permet d'interagir avec les modèles d'exploration de données existants pour établir des prédictions en fonction des données d'un tableau Excel, d'une plage Excel ou d'une autre source de données. Le processus consistant à appliquer de nouvelles données à un modèle existant pour prévoir des tendances est appelé *requête de prédiction*.  
  
 L'Assistant **Requête** propose également un éditeur avancé pour créer ou modifier des modèles d'exploration de données, pour générer des requêtes personnalisées ou pour utiliser des structures qui ne sont pas prises en charge dans les autres outils, tels que des datasets imbriqués.  
  
-   Utilisez l’éditeur de texte pour taper ou coller des instructions DMX (Data Mining Extensions) que vous avez créées ailleurs.  
  
-   Utilisez le générateur de requêtes interactif pour composer une instruction DMX personnalisée à l'aide de modèles et de boîtes de dialogue.  
  
-   Créez des instructions DMX pour gérer ou sauvegarder des structures et des modèles d'exploration de données.  
  
## <a name="using-the-query-wizard"></a>Utilisation de l'Assistant Requête  
  
1.  Tout d'abord, vous devez spécifier une source pour les données à utiliser comme entrée. Vous pouvez utiliser les données d'une plage ou d'un tableau Excel existant, ou vous pouvez spécifier une instruction SQL pour extraire les données.  
  
2.  Ensuite, l'Assistant présente la liste des modèles d'exploration de données disponibles sur le serveur auquel vous êtes connecté. Si vous savez quel modèle utiliser et que vous maîtrisez l'exploration de données, vous pouvez également cliquer sur **Avancé** pour ouvrir l' **Éditeur de requêtes avancé d'exploration de données**.  
  
3.  En fonction du type de modèle que vous choisissez, vous devez spécifier la colonne qui contient les données à évaluer et définir des mappages entre les colonnes des données d'entrée et les colonnes du modèle. En fonction de l'algorithme choisi, vous pouvez définir d'autres propriétés du modèle.  
  
4.  En dernier lieu, l'Assistant vous permet également de choisir une ou plusieurs prédictions et de spécifier une destination afin d'y stocker les résultats.  
  
 Vous pouvez à tout moment cliquer sur **Avancé** pour basculer vers l' **Éditeur de requêtes avancé d'exploration de données**qui vous permet de contrôler davantage chaque partie de l'instruction DMX. Pour plus d’informations sur l’utilisation des outils avancés de modification de requêtes, consultez [éditeur de requêtes d’exploration de données avancé](advanced-data-mining-query-editor.md).  
  
### <a name="requirements"></a>Spécifications  
 Pour utiliser l'Assistant **Requête** , vous devez être connecté à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Qui plus est, le serveur doit contenir au moins un modèle d'exploration de données d'un type approprié. Si aucun modèle d'exploration de données n'est disponible, vous pouvez en créer un à l'aide des Assistants fournis dans le Client d'exploration de données pour Excel. Pour plus d’informations sur la création d’un nouveau mode d’exploration de données à l’aide d’un Assistant, consultez [création d’un modèle d’exploration de données](creating-a-data-mining-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   
 [Client d’exploration de données pour Excel &#40;SQL Server des compléments d’exploration de données&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
