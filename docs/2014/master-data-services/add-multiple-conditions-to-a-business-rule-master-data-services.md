---
title: Ajouter plusieurs conditions à une règle d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2f9f8114186aa3593f2218037add9a0611a8fe23
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792952"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Ajouter plusieurs conditions à une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], ajoutez plusieurs conditions **AND** ou **OR** à une règle d'entreprise lorsque vous souhaitez une règle plus complexe.  
  
> [!NOTE]  
>  Si vous créez une règle d'entreprise qui utilise l'opérateur **OR** , créez une règle distincte pour chaque instruction conditionnelle qui peut être évaluée indépendamment. Vous pouvez alors exclure des règles si nécessaire, ce qui offre plus de souplesse et facilite la résolution des problèmes.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Une règle d'entreprise doit exister. Pour plus d’informations, consultez [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>Pour ajouter plusieurs conditions à une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  À partir de la **Type de membre** , sélectionnez un type de membre.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Cliquez sur la ligne de la règle d'entreprise à modifier.  
  
8.  Cliquez sur **Modifier la règle d’entreprise sélectionnée**.  
  
9. Dans le **composants** volet, développez le **opérateurs logiques** nœud.  
  
10. Cliquez sur **AND** ou **OR** et faites-la glisser vers le **IF** du volet **AND** étiquette.  
  
11. Dans le volet **Composants** , développez le nœud **Conditions** .  
  
12. Cliquez sur une condition et faites-la glisser vers **IF** volet, à la **AND** ou **OR** étiquette à partir de l’étape 10.  
  
13. Dans le **attributs** volet, cliquez sur un attribut et faites-le glisser vers le **modifier la Condition** du volet **sélectionner un attribut** étiquette.  
  
14. Dans le **modifier la Condition** volet, remplissez tous les champs requis.  
  
15. Dans le volet **Modifier la condition** , cliquez sur **Enregistrer l’élément**.  
  
16. Si vous le souhaitez, ajouter plus de conditions, à partir de la **composants** volet, faites glisser **AND** ou **OR** aux **AND** ou **OR**dans les **IF** volet. Suivez ensuite les étapes 13 à 15.  
  
    > [!TIP]  
    >  Pour supprimer une condition, cliquez sur le nom de la condition et, dans le **modifier la Condition** volet, cliquez sur **suppression de l’élément**.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Renommer une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
