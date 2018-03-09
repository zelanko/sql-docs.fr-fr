---
title: Autorisations de collection (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4423216cbc6fd28eab271c5f71957564c98e329b
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
---
# <a name="collection-permissions-master-data-services"></a>Autorisations de collection (services de données de référence)
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
  
## <a name="see-also"></a> Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
