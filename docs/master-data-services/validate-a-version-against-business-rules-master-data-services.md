---
title: "Valider une version par rapport aux r&#232;gles d&#39;entreprise (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "validation de versions [Master Data Services]"
  - "validation de versions [Master Data Services], à propos de la validation de versions"
  - "versions [Master Data Services], validation"
  - "règles d’entreprise [Master Data Services], application à tous les membres"
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Valider une version par rapport aux r&#232;gles d&#39;entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validez une version pour appliquer des règles d’entreprise à tous les membres dans la version de modèle.  
  
 Cette procédure explique comment utiliser l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour valider les données. Si vous avez l'autorisation dans la base de données MDS, vous pouvez utiliser une procédure stockée à la place. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
> [!NOTE]  
>  Tous les membres doivent passer la validation avant qu'une version puisse être validée.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions**.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   L’état de la version doit être **Ouvert** ou **Verrouillé**.  
  
-   Dans la page **Valider les versions**, les membres doivent exister avec un état autre que **Validation réussie**.  
  
### Pour valider une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions**, dans la barre de menus, cliquez sur **Valider la version**.  
  
3.  Dans la page **Valider les versions**, sélectionnez le modèle et la version à valider.  
  
4.  Cliquez sur **Valider**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Lorsque l'indicateur de progression n'est plus affiché, la validation de la version est terminée.  
  
## Étapes suivantes  
  
-   [Verrouiller une version &#40;Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md)  
  
## Voir aussi  
 [États de validation &#40;Master Data Services&#41;](../master-data-services/validation-statuses-master-data-services.md)   
 [Procédure stockée de validation &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Versions &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  