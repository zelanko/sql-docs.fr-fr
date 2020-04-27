---
title: Autorisations d’objet de modèle (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 94ad81913071a3bbd4aad33515c27c68b9e268e4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482672"
---
# <a name="model-object-permissions-master-data-services"></a>Autorisations d'objet de modèle (Master Data Services)
  Les autorisations d'objet modèle sont obligatoires. Elles déterminent les attributs auxquels un utilisateur peut accéder dans la zone fonctionnelle **Explorateur** de l'interface utilisateur.  
  
 Par exemple, si vous affectez une autorisation **Mettre à jour** sur l'entité Product, l'utilisateur peut mettre à jour tous les attributs de l'entité Product. Si vous affectez une autorisation **Mettre à jour** à un seul attribut, l'utilisateur peut mettre à jour cet attribut uniquement.  
  
 Pour déterminer la sécurité affectée sur chaque valeur d'attribut individuelle, les autorisations d'objet modèle sont associées aux autorisations des membres de la hiérarchie, qui déterminent les membres auxquels un utilisateur peut accéder.  
  
 Pour accorder à un utilisateur l’accès à une zone fonctionnelle autre que l' **Explorateur**, l’utilisateur doit être un administrateur de modèle, ce qui implique également l’attribution d’autorisations d’objet de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
 Les autorisations d’objet de modèle sont [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] affectées dans l’interface utilisateur, dans la zone fonctionnelle **autorisations d’accès** sous l’onglet **modèles** . Sous cet onglet, le modèle est représenté sous la forme d’une arborescence. Lorsque vous affectez une autorisation à un objet dans l'arborescence, tous les objets suivants héritent de cette autorisation. Vous pouvez remplacer cet héritage en affectant l'autorisation à des objets individuels.  
  
 Vous pouvez assigner des autorisations de **lecture**seule, de **mise à jour**ou de **refus** à des objets de modèle. Si vous n'affectez aucune autorisation sous l'onglet **Modèles** , l'utilisateur ne peut pas afficher les modèles ou données dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Bonne pratique  
 En général, vous devez attribuer l’autorisation **mettre à jour** à l’objet de modèle, puis attribuer explicitement l’autorisation aux objets situés sous. Si vous n'affectez pas d'autorisation aux objets en dessous, les autorisations sont héritées et l'utilisateur est un administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
