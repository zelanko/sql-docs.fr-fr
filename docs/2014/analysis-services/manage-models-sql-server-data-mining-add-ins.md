---
title: Gérer les modèles (SQL Server les compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: f37939fea1188c18079fc7e619cee6a336876e24
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541851"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a>Gérer les modèles (Compléments d'exploration de données SQL Server)
  ![Bouton Gérer les modèles, ruban Exploration de données](media/dmc-manage.gif "Bouton Gérer les modèles, ruban Exploration de données")  
  
 La boîte de dialogue **gérer les modèles** vous permet d’interagir avec les modèles d’exploration de données et les structures d’exploration de données existants qui sont stockés sur le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] serveur auquel vous êtes actuellement connecté. Vous pouvez également afficher et gérer les structures et modèles temporaires créés pendant la session active. Si vous avez utilisé à la fois les modèles de session et les modèles stockés sur un serveur, les deux sont visibles dans la boîte de dialogue.  
  
## <a name="using-the-manage-models-wizard"></a>Utilisation de l'Assistant Gérer les modèles  
 Lorsque vous cliquez sur **gérer les modèles**, la boîte de dialogue gérer les **modèles et les structures d’exploration** de données s’ouvre et fournit un accès aux fonctionnalités suivantes pour gérer les structures et modèles d’exploration de données existants :  
  
-   Renommer un modèle ou une structure d'exploration de données  
  
-   Supprimer un modèle ou une structure d'exploration de données  
  
-   Effacer un modèle ou une structure d'exploration de données  
  
-   Traiter une structure d'exploration de données à l'aide de données nouvelles ou existantes  
  
-   Exporter ou importer une structure ou un modèle d'exploration de données  
  
> [!NOTE]  
>  Cette boîte de dialogue ne vous permet pas de créer des requêtes ou des modèles. Pour créer une nouvelle structure d’exploration de données, utilisez l’un des assistants fournis dans le client d’exploration de données pour Excel ou utilisez la **requête d’exploration de données éditeur avancé**.  
  
### <a name="requirements"></a>Spécifications  
 Pour gérer des modèles d'exploration de données, créez tout d'abord une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La connexion est requise même si vous utilisez des modèles de session stockés dans un fichier temporaire. Pour plus d’informations sur la création ou la modification d’une connexion, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Si l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à laquelle vous vous connectez ne contient aucune structure d'exploration de données ni aucun modèle d'exploration de données, vous pouvez les créer en utilisant les Assistants et les autres outils fournis par ce complément. Vous pouvez également créer des modèles à l’aide du **modèle d’exploration de données éditeur avancé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
