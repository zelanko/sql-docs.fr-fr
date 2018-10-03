---
title: Afficher les erreurs qui se produisent pendant le processus de mise en lots (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8f8d6563514aec7c4e75893facb0caa8850798c9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204089"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>Afficher les erreurs qui se produisent pendant le processus de site (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez consulter les erreurs qui se produisent pendant le processus de site. La base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] comporte deux vues pour afficher les erreurs :  
  
-   stg.viw_name_MemberErrorDetails pour les mises à jour de membre feuille ou consolidé.  
  
-   stg.viw_name_RelationshipErrorDetails pour les mises à jour de relation de hiérarchie.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , vous devez disposer des autorisations SELECT sur la vue stg.viw_name_MemberErrorDetails ou stg.viw_name_RelationshipErrorDetails.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Pour afficher des erreurs de mise en lots  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Ouvrez une nouvelle requête.  
  
3.  Tapez le texte suivant, en remplaçant « name » par le nom de votre table de mise en lots, par exemple, viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Exécutez la requête. Les détails des erreurs sont affichés dans le champ **ErrorDescription** .  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur les messages d’erreur, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Importation de données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Résolution des problèmes liés au processus de site (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
