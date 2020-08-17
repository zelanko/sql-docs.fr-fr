---
description: Autorisations de collection (services de données de référence)
title: Autorisations de collection
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
ms.openlocfilehash: 04ffb34b92aa43c521a9a454a8068e74cf4fd615
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88390285"
---
# <a name="collection-permissions-master-data-services"></a>Autorisations de collection (services de données de référence)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Les autorisations de collection s'appliquent à toutes les collections d'une entité. Vous ne pouvez pas donner d'autorisation à une collection spécifique ; les autorisations s'appliquent à toutes les collections.  
  
> [!NOTE]  
>  Ces autorisations s’appliquent à la zone fonctionnelle **Explorateur** de l’interface utilisateur uniquement.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lire**|L’utilisateur peut lire les membres de collection et les attributs de membre.|  
|**Créer**|L’utilisateur peut créer des membres de collection et affecter des valeurs d’attribut.|  
|**Mettre à jour**|L’utilisateur peut mettre à jour les membres de collection, les attributs et les relations.|  
|**Supprimer**|L’utilisateur peut supprimer les membres de collection.|  
|**Deny**|Tous les accès aux membres de collection sont refusés.|  
  
 Vous pouvez aussi combiner les autorisations Read, Create, Update et Delete. Lorsque les autorisations Create, Update et Delete sont attribuées, l’autorisation Read est attribuée automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
