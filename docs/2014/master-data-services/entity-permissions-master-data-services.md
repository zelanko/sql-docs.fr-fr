---
title: Autorisations d’entité (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7add4e6562bdfff222bca289af6d7486efe4e8a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193779"
---
# <a name="entity-permissions-master-data-services"></a>Autorisations d'entité (Master Data Services)
  Les autorisations d'entité s'appliquent à :  
  
-   Les attributs de l’entité, y compris **Nom** et **Code**, pour les membres feuille et les membres consolidés.  
  
-   Les collections de l'entité.  
  
-   Appartenances et relations de hiérarchie explicites.  
  
 Lorsque vous avez une autorisation sur une entité, vous pouvez ajouter et supprimer des membres de l'entité, ses hiérarchies explicites et ses collections.  
  
> [!NOTE]  
>  Ces autorisations s’appliquent à la zone fonctionnelle **Explorateur** de l’interface utilisateur uniquement.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|L'entité est affichée, mais l'utilisateur ne peut pas ajouter, supprimer ni modifier des membres.|  
|**Update**|L'entité est affichée et l'utilisateur peut ajouter, supprimer et modifier des membres.|  
|**Refuser**|L'entité n'est pas affichée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Entités (Master Data Services)](../../2014/master-data-services/entities-master-data-services.md)  
  
  
