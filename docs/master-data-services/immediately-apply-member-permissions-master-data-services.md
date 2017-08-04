---
title: "Appliquer immédiatement des autorisations de membre (Master Data Services) | Documents Microsoft"
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
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1549958a5c84045eccbb52c5fac2f2f2b09d316e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="immediately-apply-member-permissions-master-data-services"></a>Appliquer immédiatement des autorisations de membre (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], au lieu d'attendre que la sécurité des membres s'applique à intervalles réguliers, vous pouvez appliquer immédiatement des autorisations de membre.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'exécuter la procédure stockée mdm.udpSecurityMemberProcessRebuildModel dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Pour plus d’informations, consultez [Sécurité de l’objet de base de données &#40;Master Data Services&#41;](../master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a>Pour appliquer immédiatement des autorisations de membres de la hiérarchie  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Créez une requête.  
  
3.  Tapez le texte suivant, en remplaçant *database* par le nom de votre base de données et *Model_Name* par le nom du modèle.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  Exécute la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations des membres de hiérarchie &#40; Master Data Services &#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Autorisations des membres de hiérarchie &#40; Master Data Services &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
