---
title: Autorisations des membres de la hiérarchie (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 371c7c605b5415654c01f3faa66fbd0801202785
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482952"
---
# <a name="hierarchy-member-permissions-master-data-services"></a>Autorisations des membres de la hiérarchie (Master Data Services)
  Les autorisations des membres de la hiérarchie sont optionnelles et doivent être utilisées uniquement lorsque vous souhaitez qu'un utilisateur ait un accès limité à des membres spécifiques. Si vous n'affectez pas d'autorisations sous l'onglet **Membres de hiérarchie** , les autorisations de l'utilisateur sont basées uniquement sur celles affectées sous l'onglet **Modèles** .  
  
 Les autorisations des membres de la hiérarchie [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sont affectées dans l’interface utilisateur, dans la zone fonctionnelle **autorisations d’accès** sous l’onglet **membres de hiérarchie** . Ces autorisations déterminent les membres auxquels un utilisateur peut accéder dans la zone fonctionnelle **Explorateur** de l’interface utilisateur.  
  
 Sous l'onglet **Membres de hiérarchie** , chaque hiérarchie est représentée comme une arborescence. Lorsque vous affectez une autorisation à un nœud dans l'arborescence, tous les enfants héritent de cette autorisation à moins qu'elle ne soit affectée explicitement à un niveau inférieur.  
  
> [!NOTE]  
>  Lorsque vous affectez une autorisation à un nœud dans une hiérarchie, tous les membres des autres nœuds au même niveau ou à un niveau supérieur sont implicitement refusés.  
  
 Dans l' **Explorateur**, les autorisations des membres sont appliquées partout où le membre est affiché. Par exemple, un membre avec l’autorisation **lecture** seule est en lecture seule dans toutes les entités, hiérarchies et collections auxquelles il appartient.  
  
 Les autorisations des membres de la hiérarchie s'appliquent à la version de modèle à laquelle vous les affectez ainsi qu'à toutes les futures copies de la version. Elles ne s'appliquent pas aux versions antérieures à celle à laquelle vous les affectez.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|Les membres sont affichés, mais l'utilisateur ne peut pas les modifier. L'utilisateur ne peut pas non plus déplacer les membres dans les collections ou hiérarchies explicites auxquelles les membres appartiennent.<br /><br /> Remarque : Si vous attribuez l’autorisation **lecture** seule à la **racine**, les membres sous **racine** sont en lecture seule ; Toutefois, dans les hiérarchies et collections explicites, l’utilisateur peut déplacer des membres vers la **racine** et ajouter de nouveaux membres à la **racine**.|  
|**Mise à jour**|Les membres sont affichés et l'utilisateur peut les modifier. L'utilisateur peut également déplacer les membres dans les collections ou hiérarchies explicites auxquelles les membres appartiennent.|  
|**Deny**|Les membres ne sont pas affichés.|  
  
 Sous l'onglet **Membres de hiérarchie** , les autorisations que vous affectez n'entrent pas immédiatement en vigueur. La fréquence à laquelle les autorisations sont appliquées dépend du paramètre **Intervalle de traitement de la sécurité des membres** dans la table Paramètres système de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Vous pouvez appliquer immédiatement des autorisations de membre en suivant la procédure décrite dans [Appliquer immédiatement des autorisations de membre &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas affecter d'autorisations de membre de hiérarchie à des hiérarchies récursives, des hiérarchies dérivées avec un niveau supérieur composé d'une hiérarchie explicite et des hiérarchies dérivées avec des niveaux masqués.  
  
## <a name="possible-overlapping-permissions"></a>Possibilité de chevauchement des autorisations  
 Lorsque vous affectez une autorisation aux membres, vous devrez peut-être résoudre des problèmes de chevauchement des autorisations.  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a>Lorsqu'un membre appartient à plusieurs hiérarchies  
 Plusieurs hiérarchies peuvent contenir le même membre.  
  
-   Si une autorisation **mettre à jour** est affectée à un nœud de la hiérarchie et que l’autre est **accessible en lecture seule**, les membres du nœud sont **en lecture**seule.  
  
-   Si l’autorisation **mise à jour** ou **lecture seule** est affectée à un nœud de la hiérarchie et que l’autorisation **refuser**est affectée à un autre nœud, les membres du nœud ne sont pas affichés.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Membres &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Hiérarchies &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md)   
 [Appliquer immédiatement des autorisations de membre &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md)  
  
  
