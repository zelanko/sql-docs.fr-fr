---
title: Approbation requise
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 61d03410e5217175335caf0ca37241b28c887989
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729756"
---
# <a name="approval-required-master-data-services"></a>Approbation requise (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], l’administrateur peut définir une entité sur Approbation requise. Toutes les modifications apportées à cette entité nécessitent que l’un des administrateurs d’entité les vérifie et les approuve.  
  
> [!NOTE]  
>  Les modifications effectuées sur les membres feuille exigent une approbation. Les modifications apportées aux hiérarchies et aux collections explicitement déconseillées contournent l’approbation.  
>   
>  Les modifications apportées au travers du processus de table de mise en lots contournent l’approbation.  
>   
>  Les modifications apportées par une règle d’entreprise contournent l’approbation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Administration de système  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une entité doit exister. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="to-enable-approval-required-for-an-entity"></a>Pour activer l’option Approbation requise pour une entité  
  
1.  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la grille de la page **Gérer le modèle** , sélectionnez un modèle et cliquez sur **Entités**.  
  
3.  Dans la grille de la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez activer  **Approbation requise** .  
  
4.  Cliquez sur **Modifier**, sélectionnez **Approbation requise**, puis cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de modifications &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  
