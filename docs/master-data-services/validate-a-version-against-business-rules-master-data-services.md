---
description: Valider une version par rapport aux règles d'entreprise (Master Data Services)
title: Valider une version par rapport aux règles d'entreprise
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
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
ms.openlocfilehash: 676a6fff88de31480737f1bb82cc0466605b4699
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88388315"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>Valider une version par rapport aux règles d'entreprise (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validez une version pour appliquer des règles d’entreprise à tous les membres dans la version de modèle.  
  
 Cette procédure explique comment utiliser l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour valider les données. Si vous avez l'autorisation dans la base de données MDS, vous pouvez utiliser une procédure stockée à la place. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Tous les membres doivent passer la validation avant qu'une version puisse être validée.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
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
  
-   [Verrouiller une version &#40;Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [États de validation &#40;Master Data Services&#41;](../master-data-services/validation-statuses-master-data-services.md)   
 [&#40;de la procédure stockée de validation Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Versions &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [&#40;des règles d’entreprise Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
