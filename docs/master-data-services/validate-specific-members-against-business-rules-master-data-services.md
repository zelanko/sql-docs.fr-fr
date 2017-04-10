---
title: "Valider des membres sp&#233;cifiques par rapport aux r&#232;gles d&#39;entreprise (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "application de règles d'entreprise [Master Data Services]"
  - "règles d’entreprise [Master Data Services], application à des membres sélectionnés"
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Valider des membres sp&#233;cifiques par rapport aux r&#232;gles d&#39;entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], appliquez des règles d'entreprise sélectivement lorsque vous souhaitez mettre à jour ou valider des sous-ensembles de membres par rapport à des règles d'entreprise.  
  
> [!NOTE]  
>  Si vous souhaitez appliquer des règles d’entreprise à tous les membres dans une version d’un modèle, consultez [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez au minimum disposer de l'autorisation **Mettre à jour** sur l'objet modèle auquel vous appliquez les règles d'entreprise.  
  
### Pour appliquer des règles d'entreprise sélectivement  
  
1.  Dans la page d’accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], dans la liste déroulante **Modèle**, sélectionnez un modèle.  
  
2.  Dans la liste déroulante **Version**, sélectionnez une version.  
  
3.  Cliquez sur l’onglet **Explorateur** .  
  
4.  Dans la barre de menus, pointez sur **Entités** , puis cliquez sur le nom de l'entité qui contient les membres auxquels vous souhaitez appliquer les règles.  
  
5.  Cliquez sur **Appliquer les règles**. Les règles d'entreprise sont appliquées uniquement aux membres affichés dans la grille.  
  
## Voir aussi  
 [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  