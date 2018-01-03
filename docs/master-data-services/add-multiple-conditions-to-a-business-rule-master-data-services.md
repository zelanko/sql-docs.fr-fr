---
title: "Ajouter plusieurs conditions à une règle d’entreprise (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
caps.latest.revision: "9"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ab40c3eda3f93bcee19f9d1de4faa0b6f0b6ecb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Ajouter plusieurs conditions à une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], ajoutez plusieurs conditions **AND** ou **OR** à une règle d'entreprise lorsque vous souhaitez une règle plus complexe.  
  
> [!NOTE]  
>  Si vous créez une règle d'entreprise qui utilise l'opérateur **OR** , créez une règle distincte pour chaque instruction conditionnelle qui peut être évaluée indépendamment. Vous pouvez alors exclure des règles si nécessaire, ce qui offre plus de souplesse et facilite la résolution des problèmes.  
  
## <a name="prerequisites"></a>Prerequisites  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une règle d'entreprise doit exister. Pour plus d’informations, consultez [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>Pour ajouter plusieurs conditions à une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Règles d’entreprise/** , sélectionnez un modèle dans la liste déroulante **Modèle** .  
  
4.  Dans la liste déroulante **Entité** , sélectionnez une entité.  
  
5.  Dans la liste déroulante **Types de membres** , sélectionnez un type de membre.  
  
6.  Cliquez sur la ligne de la règle d'entreprise à modifier.  
  
7.  Cliquez sur **Modifier**.  
  
8.  Sous le bloc **If** à gauche de la liste déroulante, sélectionnez l’opérateur logique **AND/OR/NOT**dans la liste.  
  
9. Cliquez sur **Ajouter**. Un panneau s’affiche.  
  
10. Dans la liste déroulante **Attribut** , sélectionnez un attribut.  
  
11. Dans la liste déroulante **Opérateur** , sélectionnez une condition.  
  
12. Complétez tous les champs obligatoires.  
  
13. Cliquez sur **Enregistrer**. Une nouvelle ligne est ajoutée à la grille **If** .  
  
14. Si vous le souhaitez, suivez les étapes 8 à 13 pour ajouter d’autres conditions.  
  
    > [!TIP]  
    >  Pour supprimer une condition, sélectionnez-la, cliquez dessus avec le bouton droit, puis cliquez sur **Supprimer**.  
  
    > [!TIP]  
    >  Vous pouvez sélectionner plusieurs conditions et, à l’aide d’un clic droit, les regrouper dans un opérateur logique ou les dissocier à l’intérieur d’un opérateur logique spécifique.  
  
## <a name="see-also"></a> Voir aussi  
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Renommer une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
