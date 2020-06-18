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
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf135e4c1f67a7187ec67284d52adcdb25c9bd27
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972279"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>Ajouter plusieurs conditions à une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], ajoutez plusieurs conditions **AND** ou **OR** à une règle d'entreprise lorsque vous souhaitez une règle plus complexe.  
  
> [!NOTE]  
>  Si vous créez une règle d'entreprise qui utilise l'opérateur **OR** , créez une règle distincte pour chaque instruction conditionnelle qui peut être évaluée indépendamment. Vous pouvez alors exclure des règles si nécessaire, ce qui offre plus de souplesse et facilite la résolution des problèmes.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Une règle d'entreprise doit exister. Pour plus d’informations, consultez [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>Pour ajouter plusieurs conditions à une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **type de membre** , sélectionnez un type de membre.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Cliquez sur la ligne de la règle d'entreprise à modifier.  
  
8.  Cliquez sur **Modifier la règle d’entreprise sélectionnée**.  
  
9. Dans le volet **composants** , développez le nœud **opérateurs logiques** .  
  
10. Cliquez sur **et** ou **ou** , puis faites-le glisser vers l’étiquette **et** le du volet **If** .  
  
11. Dans le volet **Composants** , développez le nœud **Conditions** .  
  
12. Cliquez sur une condition et faites-la glisser vers le volet **If** , vers l’étiquette **et** **ou ou à** partir de l’étape 10.  
  
13. Dans le volet **attributs** , cliquez sur un attribut et faites-le glisser vers l’étiquette **Sélectionner un attribut** du volet **modifier la condition** .  
  
14. Dans le volet **modifier la condition** , complétez tous les champs obligatoires.  
  
15. Dans le volet **Modifier la condition** , cliquez sur **Enregistrer l’élément**.  
  
16. Si vous le souhaitez, pour ajouter d’autres conditions, à partir du volet **composants** , faites glisser **and** ou **or** vers Any **et** or **ou** dans le volet **If** . Suivez ensuite les étapes 13 à 15.  
  
    > [!TIP]  
    >  Pour supprimer une condition, cliquez sur le nom de la condition, puis dans le volet **modifier la condition** , cliquez sur **Supprimer l’élément**.  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;des règles d’entreprise Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Modifier le nom d’une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
