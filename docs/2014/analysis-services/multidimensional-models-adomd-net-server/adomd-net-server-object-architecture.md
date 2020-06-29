---
title: Architecture des objets serveur ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33a8f420f985c9e62c7d7f275e7de370a6988e8d
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469054"
---
# <a name="adomdnet-server-object-architecture"></a>Architecture des objets serveur ADOMD.NET
  Les objets serveur ADOMD.NET sont des objets d’assistance qui peuvent être utilisés pour créer des fonctions définies par l’utilisateur (UDF) ou des procédures stockées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
> [!NOTE]  
>  Pour utiliser l'espace de noms `Microsoft.AnalysisServices.AdomdServer` (et ces objets), une référence à msmgdsrv.dll doit être ajoutée au projet UDF ou à la procédure stockée.  
  
 ![Affiche les relations d'objet dans le serveur ADOMD.NET](../../analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "Affiche les relations d'objet dans le serveur ADOMD.NET")  
Modèle objet ADOMD.NET  
  
 L'interaction avec la hiérarchie d'objets ADOMD.NET débute généralement avec un ou plusieurs objets de la couche de niveau supérieur, comme indiqué dans le tableau suivant.  
  
|À|Utiliser cet objet|  
|--------|---------------------|  
|Évaluer des instructions MDX (Multidimensional Expressions)|[Microsoft. AnalysisServices. AdomdServer. expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))<br /> L’objet [Microsoft. AnalysisServices. AdomdServer. expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) offre un moyen d’exécuter une expression MDX et d’évaluer cette expression sous un tuple spécifié.|  
|Offrir la possibilité d'exécuter des fonctions MDX sans construire l'instruction MDX entière|[Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))<br /> L’objet [Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) est pratique pour appeler des fonctions MDX prédéfinies sans utiliser l’objet [Microsoft. AnalysisServices. AdomdServer. expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) . Des fonctions supplémentaires pour l’objet [Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) doivent être disponibles dans les versions ultérieures.|  
|Représenter le contexte d'exécution actuel pour la fonction définie par l'utilisateur|[Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))<br /> L’objet [Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) expose des informations telles que le cube ou le modèle d’exploration de données actuel et diverses collections de métadonnées. L’une des principales utilisation de l’objet [Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) est la propriété [Microsoft. AnalysisServices. AdomdServer. Hierarchy. CurrentMember *](/previous-versions/sql/sql-server-2014/ms137044(v=sql.120)) de l’objet [Microsoft. AnalysisServices. AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120)) . Cette utilisation clé permet à l'auteur de la fonction définie par l'utilisateur ou de la procédure stockée de prendre des décisions en fonction du membre d'une certaine dimension sur lequel la requête porte.|  
|Créer des ensembles et des tuples|[Microsoft. AnalysisServices. AdomdServer. SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)), [Microsoft. AnalysisServices. AdomdServer. TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))<br /> [Microsoft. AnalysisServices. AdomdServer. SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)) fournit un moyen de créer des ensembles immuables, tandis que [Microsoft. AnalysisServices. AdomdServer. TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120)) fournit un moyen de créer des tuples immuables.|  
|Prendre en charge une conversion implicite entre les six types de base du langage MDX|[Microsoft. AnalysisServices. AdomdServer. MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))<br /> L’objet [Microsoft. AnalysisServices. AdomdServer. MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120)) fournit une conversion implicite et un cast parmi les types suivants :<br /><br /> -   [Microsoft. AnalysisServices. AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Level](/previous-versions/sql/sql-server-2014/ms143581(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Member](/previous-versions/sql/sql-server-2014/ms143820(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Tuple](/previous-versions/sql/sql-server-2014/ms145330(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Set](/previous-versions/sql/sql-server-2014/ms144530(v=sql.120))<br />-Scalaires ou types valeur|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du serveur ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
