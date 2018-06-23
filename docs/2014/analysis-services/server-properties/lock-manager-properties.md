---
title: Propriétés du Gestionnaire de verrous | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- lock manager properties [Analysis Services]
- LockWaitGranularityMS property
- DefaultLockTimeoutMS property
- DeadlockDetectionGranularityMS property
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 39b1c209bb8993483628af89ac7e80b558862436
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044814"
---
# <a name="lock-manager-properties"></a>Propriétés du gestionnaire de verrous
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés du serveur du gestionnaire de verrous répertoriées dans le tableau suivant. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## <a name="properties"></a>Propriétés  
 `DefaultLockTimeoutMS`  
 Propriété dont la valeur est un entier 32 bits signé qui définit le délai d'expiration de verrouillage par défaut (en millisecondes) pour les demandes de verrous internes.  
  
 La valeur par défaut de cette propriété est -1, qui indique l'absence de délai d'expiration pour les demandes de verrous internes.  
  
 `LockWaitGranularityMS`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DeadlockDetectionGranularityMS`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d’une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  