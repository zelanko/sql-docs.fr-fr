---
title: "Les fonctionnalités de Master Data Services déconseillées | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
caps.latest.revision: 18
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e4d9b433e72c916ae6611520498b0eb8fa85c8f6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="deprecated-master-data-services-features"></a>Fonctionnalités Master Data Services déconseillées
  Cette rubrique décrit les fonctionnalités [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="explicit-hierarchies-collections-and-related-components"></a>Hiérarchies explicites, collections et composants associés  
 Les hiérarchies explicites, collections et composants associés sont déconseillés. Les membres qui auparavant étaient modélisés comme des membres consolidés (parents de hiérarchie explicite) et des collections seront modélisés comme des membres feuille dans les hiérarchies dérivées. Les nouvelles fonctionnalités suivantes permettent aux hiérarchies dérivées de prendre la place des hiérarchies explicites.  
  
-   Les hiérarchies dérivées récursives servent maintenant à affecter des autorisations de sécurité aux membres.  
  
     Une hiérarchie explicite est analogue à une hiérarchie dérivée récursive avec un seul niveau non récursif sous le niveau récursif. Une hiérarchie dérivée récursive peut être complexe, en incluant un ou plusieurs niveaux au-dessous et/ou au-dessus d’un niveau récursif.  
  
-   Dans l’Explorateur, la page des hiérarchies dérivées affiche maintenant les membres non attribués (inutilisés) pour chaque niveau hiérarchique. Les nœuds inutilisés sont regroupés par niveau hiérarchique. Les membres peuvent être déplacés entre les nœuds racine et inutilisés par glisser-déplacer ou couper-coller.  
  
     Dans Administration de système, les nœuds inutilisés s’affichent dans le volet **Aperçu** . Dans Sécurité, les nœuds inutilisés s’affichent dans le volet **Autorisations des membres de la hiérarchie** . Tout membre, qu’il soit sous le nœud **Racine** ou **Inutilisé** , peut se voir attribuer une autorisation. Les pseudo-membres **Racine**, **Inutilisé**et **Inutilisé** peuvent également se voir attribuer des autorisations.  
  
-   La procédure stockée mdm.udpConvertCollectionAndConsolidatedMembersToLeaf convertit les hiérarchies explicites en hiérarchies dérivées récursives, ainsi que les membres consolidés et de collection en membres feuille.  
  
     Les hiérarchies explicites ainsi que les membres consolidés et de collection, restent pris en charge. l’exécution de la procédure stockée est donc facultative. Toutefois, si vous utilisez ces éléments, il est recommandé d’exécuter la procédure stockée, car ils sont déconseillés.  
  
 Pour plus d’informations sur les hiérarchies explicites, les collections et les membres consolidés, consultez les rubriques suivantes.  
  
-   [Hiérarchies explicites &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [Membres &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
## <a name="attribute-entity-transaction-log-type"></a>Type de journal des transactions d’entité Attribut  
Le type de journal des transactions d’entité « Attribut » est déconseillé. Migrez vers le type de journal des transactions d’entité « Membre ». Pour plus d’informations sur les types de journaux des transactions d’entité, consultez la rubrique suivante :
* [Modifier le type du journal des transactions de l’entité (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)
* [Historique de révision de membre](../master-data-services/member-revision-history-master-data-services.md)
  
## <a name="external-resources"></a>Ressources externes  
 Billet de blog [Deprecated: Explicit Hierarchies and Collections](http://go.microsoft.com/fwlink/p/?LinkId=615373)sur msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités Master Data Services éliminées](../master-data-services/discontinued-master-data-services-features.md)  
  
  
