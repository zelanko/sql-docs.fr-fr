---
title: "Requ&#233;rir des valeurs d&#39;attribut (Master Data Services) | Microsoft Docs"
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
  - "règles d’entreprise [Master Data Services], exigence de valeurs d’attribut"
  - "attributs [Master Data Services], exigence de valeurs"
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Requ&#233;rir des valeurs d&#39;attribut (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], requérez des valeurs d'attribut lorsque vous souhaitez vérifier que vos données de référence sont complètes.  
  
> [!NOTE]  
>  Les membres sans valeurs d'attribut basé sur un domaine ne sont pas affichés dans les hiérarchies dérivées basées sur ces relations.  
  
## Configuration requise  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs & #40 ; Master Data Services & #41 ;](../master-data-services/administrators-master-data-services.md).  
  
### Pour requérir des valeurs d'attribut  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Sur le **les règles d’entreprise** page, à partir de la **modèle** la liste déroulante, sélectionnez un modèle.  
  
4.  À partir de la **entité** la liste déroulante, sélectionnez une entité.  
  
5.  À partir de la **des Types de membres** la liste déroulante, sélectionnez le type de membre pour la règle d’entreprise à appliquer à.  
  
6.  Cliquez sur **Ajouter**.  
  
7.  Dans la zone **Nom** , tapez un nom de règle d’entreprise.  
  
8.  Si vous le souhaitez, dans le champ **Description** , tapez la description de la règle d’entreprise.  
  
9. Sous le bloc **Then** , cliquez sur le bouton **Ajouter**. Un panneau s’affiche.  
  
10. À partir de la **opérateur** la liste déroulante, sélectionnez **requis action**.  
  
11. À partir de la **attribut** la liste déroulante, sélectionnez un attribut.  
  
12. Cliquez sur **Enregistrer**. Une nouvelle ligne est ajoutée à la grille **Then** .  
  
13. Cliquez sur **Enregistrer**.  
  
14. Cliquez sur **Tout publier**.  
  
15. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur de la colonne **État de la règle d’entreprise** est **Active**.  
  
## Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport à des règles d’entreprise & #40 ; Master Data Services & #41 ;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une Version par rapport à des règles d’entreprise & #40 ; Master Data Services & #41 ;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## Voir aussi  
 [Les règles d’entreprise & #40 ; Master Data Services & #41 ;](../master-data-services/business-rules-master-data-services.md)   
 [Hiérarchies dérivées & #40 ; Master Data Services & #41 ;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  