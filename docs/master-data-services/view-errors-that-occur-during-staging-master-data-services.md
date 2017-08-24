---
title: Afficher les erreurs qui se produisent pendant la mise en lots (Master Data Services) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3a5ecc701aa1eab2162c41724b3a7a3319d8eb68
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="view-errors-that-occur-during-staging-master-data-services"></a>Afficher les erreurs rencontrées lors de la mise en lots (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez consulter les erreurs qui se produisent pendant le processus de site. La base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] comporte deux vues pour afficher les erreurs :  
  
-   stg.viw_name_MemberErrorDetails pour les mises à jour de membre feuille ou consolidé.  
  
-   stg.viw_name_RelationshipErrorDetails pour les mises à jour de relation de hiérarchie.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , vous devez disposer des autorisations SELECT sur la vue stg.viw_name_MemberErrorDetails ou stg.viw_name_RelationshipErrorDetails.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Pour afficher des erreurs de mise en lots  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Ouvrez une nouvelle requête.  
  
3.  Tapez le texte suivant, en remplaçant « name » par le nom de votre table de mise en lots, par exemple, viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Exécutez la requête. Les détails des erreurs sont affichés dans le champ **ErrorDescription** .  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur les messages d’erreur, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : importation de données à partir de tables &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Résolution des problèmes liés au processus de site (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
