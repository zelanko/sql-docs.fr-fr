---
title: Modifier le compte d’administrateur système (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 593e71b63cb4fc6e63c1c087e62f24c37c399e8e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069937"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Modifier le compte de l'administrateur système (Master Data Services)
  Vous pouvez modifier le compte d’utilisateur qui est désigné comme le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] administrateur système.  
  
> [!WARNING]  
>  Une fois cette procédure terminée, le compte d'administrateur système précédent est supprimé.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez ajouter le nom d'utilisateur du nouvel administrateur à la liste d'utilisateurs de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Pour plus d’informations, consultez [ajouter un utilisateur &#40;Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   Vous devez avoir l'autorisation d'afficher mdm.tblUse et d'exécuter la procédure stockée mdm.udpSecurityMemberProcessRebuildModel dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Pour plus d’informations, consultez [Sécurité de l’objet de base de données &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>Pour modifier le compte d'administrateur  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l’instance [!INCLUDE[ssDE](../includes/ssde-md.md)] pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Dans mdm.tblUser, recherchez l’utilisateur qui sera le nouvel administrateur et copiez la valeur dans la `SID` colonne.  
  
3.  Créez une requête.  
  
4.  Tapez le texte suivant, en remplaçant *domaine\nom_utilisateur* avec le nouveau nom d’utilisateur administrateur et *SID* avec la valeur que vous avez copié à l’étape 2.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Exécute la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Les administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
