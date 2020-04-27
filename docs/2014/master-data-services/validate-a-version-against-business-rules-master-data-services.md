---
title: Valider une version par rapport aux règles d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e33526df02cff22adbd56bfbfc2f25cef1c1c052
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482308"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>Valider une version par rapport aux règles d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validez une version pour appliquer des règles d’entreprise à tous les membres dans la version de modèle.  
  
 Cette procédure explique comment utiliser l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour valider les données. Si vous avez l'autorisation dans la base de données MDS, vous pouvez utiliser une procédure stockée à la place. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Tous les membres doivent passer la validation avant qu'une version puisse être validée.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   L’état de la version doit être **Ouvert** ou **Verrouillé**.  
  
-   Dans la page **Valider les versions** , les membres doivent exister avec un état autre que **Validation réussie**.  
  
### <a name="to-validate-a-version"></a>Pour valider une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions** , dans la barre de menus, cliquez sur **Valider la version**.  
  
3.  Dans la page **Valider les versions** , sélectionnez le modèle et la version à valider.  
  
4.  Cliquez sur **Valider**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Lorsque l'indicateur de progression n'est plus affiché, la validation de la version est terminée.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Verrouiller une version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [États de validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md)   
 [&#40;de la procédure stockée de validation Master Data Services&#41;](validation-stored-procedure-master-data-services.md)   
 [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [&#40;des règles d’entreprise Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
