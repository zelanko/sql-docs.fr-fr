---
title: Gérer les modèles (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb7fee7425db1e22cd8db59477fb0bf30ce1d01c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225369"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a>Gérer les modèles (Compléments d'exploration de données SQL Server)
  ![Bouton de gérer les modèles, ruban Exploration de données](media/dmc-manage.gif "bouton de gérer les modèles, ruban Exploration de données")  
  
 Le **gérer les modèles** boîte de dialogue vous permet d’interagir avec les modèles d’exploration de données existants et les structures d’exploration de données qui sont stockés dans le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] serveur auquel vous êtes actuellement connecté. Vous pouvez également afficher et gérer les structures et modèles temporaires créés pendant la session active. Si vous avez utilisé à la fois les modèles de session et les modèles stockés sur un serveur, les deux sont visibles dans la boîte de dialogue.  
  
## <a name="using-the-manage-models-wizard"></a>Utilisation de l'Assistant Gérer les modèles  
 Lorsque vous cliquez sur **gérer les modèles**, le **gérer les Structures d’exploration de données et des modèles** boîte de dialogue s’ouvre, fournissant l’accès aux fonctionnalités suivantes pour la gestion des modèles d’exploration de données et des structures existants :  
  
-   Renommer un modèle ou une structure d'exploration de données  
  
-   Supprimer un modèle ou une structure d'exploration de données  
  
-   Effacer un modèle ou une structure d'exploration de données  
  
-   Traiter une structure d'exploration de données à l'aide de données nouvelles ou existantes  
  
-   Exporter ou importer une structure ou un modèle d'exploration de données  
  
> [!NOTE]  
>  Cette boîte de dialogue ne vous permet pas de créer des requêtes ou des modèles. Pour créer une nouvelle structure d’exploration de données, utilisez un des Assistants fournis dans le Client d’exploration de données pour Excel, ou utilisez le **éditeur avancé de requête d’exploration de données**.  
  
### <a name="requirements"></a>Spécifications  
 Pour gérer des modèles d'exploration de données, créez tout d'abord une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La connexion est requise même si vous utilisez des modèles de session stockés dans un fichier temporaire. Pour plus d’informations sur la création ou modification d’une connexion, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Si l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à laquelle vous vous connectez ne contient aucune structure d'exploration de données ni aucun modèle d'exploration de données, vous pouvez les créer en utilisant les Assistants et les autres outils fournis par ce complément. Vous pouvez également créer de nouveaux modèles à l’aide de la **d’exploration de données modèle Éditeur avancé de données**.  
  
## <a name="see-also"></a>Voir aussi  
 [Les modèles d’exploration de données de documentation &#40;les données des compléments d’exploration de données pour Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les données des compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
