---
title: Autorisations consolidées (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b40598eaa81ce0a1d890ef8ec37a12fada0fa458
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971899"
---
# <a name="consolidated-permissions-master-data-services"></a>Autorisations consolidées (services de données de référence)
  Les autorisations consolidées s'appliquent aux valeurs d'attribut pour tous les membres consolidés d'une entité.  
  
 Les autorisations consolidées s'appliquent uniquement aux entités activées pour les hiérarchies explicites et les collections.  
  
 **Remarques :**  
  
-   Les autorisations de feuille s'appliquent à la zone fonctionnelle **Explorateur** de l'interface utilisateur uniquement.  
  
-   Les autorisations attribuées à **Nom** et **Code** ne sont pas appliquées.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|Les membres consolidés sont affichés, mais l'utilisateur ne peut pas les ajouter, les supprimer ni les modifier.|  
|**Update**|Les membres consolidés sont affichés et l'utilisateur peut les ajouter, les supprimer et les modifier.|  
|**Deny**|Les membres consolidés pour l'entité ne sont pas affichés.|  
  
## <a name="attribute-permissions"></a>Autorisations d'attribut  
 Les autorisations d’attribut s’appliquent aux valeurs de l’attribut pour l’entité spécifique. Les utilisateurs avec uniquement des autorisations d'attribut ne peuvent pas ajouter ni supprimer des membres.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|L'attribut est affiché, mais l'utilisateur ne peut pas modifier les valeurs d'attribut.|  
|**Update**|L'attribut est affiché et l'utilisateur peut modifier les valeurs d'attribut.|  
|**Deny**|L'attribut n'est pas affiché.<br /><br /> Remarque : vous ne pouvez pas refuser explicitement l’accès aux attributs Name et Code.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Autorisations feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Membres &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
