---
title: Propriétés du Gestionnaire de verrous Analysis Services | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a5383fe83963a9b388413b9b829b4fac7fc11788
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071586"
---
# <a name="lock-manager-properties"></a>Propriétés du gestionnaire de verrous
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés du serveur du gestionnaire de verrous répertoriées dans le tableau suivant. Pour plus d’informations sur les autres propriétés de serveur et sur la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **S’applique à :** Mode serveur multidimensionnel et tabulaire  
  
## <a name="properties"></a>Properties  
 **DefaultLockTimeoutMS**  
 Propriété dont la valeur est un entier 32 bits signé qui définit le délai d'expiration de verrouillage par défaut (en millisecondes) pour les demandes de verrous internes.  
  
 La valeur par défaut de cette propriété est -1, qui indique l'absence de délai d'expiration pour les demandes de verrous internes.  
  
 **LockWaitGranularityMS**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DeadlockDetectionGranularityMS**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
