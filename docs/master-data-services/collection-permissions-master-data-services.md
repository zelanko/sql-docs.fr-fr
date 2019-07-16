---
title: Autorisations de collection (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7e2e1dbbf51533e03d3e1f5a6930dd0a022cf215
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941103"
---
# <a name="collection-permissions-master-data-services"></a>Autorisations de collection (services de données de référence)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Les autorisations de collection s'appliquent à toutes les collections d'une entité. Vous ne pouvez pas donner d'autorisation à une collection spécifique ; les autorisations s'appliquent à toutes les collections.  
  
> [!NOTE]  
>  Ces autorisations s’appliquent à la zone fonctionnelle **Explorateur** de l’interface utilisateur uniquement.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture**|L’utilisateur peut lire les membres de collection et les attributs de membre.|  
|**Créer**|L’utilisateur peut créer des membres de collection et affecter des valeurs d’attribut.|  
|**Update**|L’utilisateur peut mettre à jour les membres de collection, les attributs et les relations.|  
|**Supprimer**|L’utilisateur peut supprimer les membres de collection.|  
|**Refuser**|Tous les accès aux membres de collection sont refusés.|  
  
 Vous pouvez combiner les autorisations d’accès en lecture, de création, de mise à jour et de suppression. Lorsque les autorisations Create, Update et Delete sont attribuées, l’autorisation Read est attribuée automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
