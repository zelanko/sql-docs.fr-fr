---
title: "Exclure une r&#232;gle d&#39;entreprise (Master Data Services) | Microsoft Docs"
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
  - "règles d’entreprise [Master Data Services], exclusion"
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Exclure une r&#232;gle d&#39;entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], excluez une règle d'entreprise lorsque vous ne voulez pas supprimer la règle définitivement, mais que vous ne souhaitez pas valider des données par rapport à elle.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Pour exclure une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Règles d’entreprise**, sélectionnez un modèle dans la liste déroulante **Modèle**.  
  
4.  Dans la liste déroulante **Entité**, sélectionnez une entité.  
  
5.  Dans la liste déroulante **Types de membres**, sélectionnez un type de membre.  
  
6.  Dans la grille, sélectionnez la ligne pour la règle d’entreprise à exclure et cliquez sur **Modifier**.  
  
7.  Cochez la case **Exclu**.  
  
8.  Cliquez sur **Enregistrer**.  
  
9. Cliquez sur **Tout publier**.  
  
10. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur de la colonne **État de la règle d’entreprise** est **Exclu** et celle de la colonne **Exclu** est **Oui**.  
  
## Voir aussi  
 [Supprimer une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  