---
title: Démarrer des actions en fonction de modifications de valeurs d’attribut (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2f66a7e91bcb475fe72d6abbe9f6007c8b9d668b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275535"
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a>Initier des actions en fonction de modifications de valeurs d'attribut (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une règle d’entreprise pour initier des actions en fonction des modifications apportées aux valeurs d’attribut. Par exemple, lorsqu'une valeur d'attribut spécifique change, vous pouvez modifier une valeur, envoyer une notification, ou démarrer un flux de travail externe.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Vos attributs doivent se trouver dans un groupe de suivi des modifications. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) .  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a>Pour créer une règle d'entreprise afin d'initier des actions en fonction des modifications apportées aux valeurs d'attribut.  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **Type de membre** , sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Cliquez sur **Ajouter une règle d’entreprise**.  
  
8.  Cliquez sur **Modifier la règle d’entreprise sélectionnée**.  
  
9. Dans le volet **Composants** , développez le nœud **Conditions** .  
  
10. Sous le nœud **Comparaison de valeur** , faites glisser **a changé** vers l’étiquette **Conditions** du volet **IF** .  
  
11. Dans le **attributs** volet, cliquez sur un attribut et faites-le glisser vers le **modifier la Condition** du volet **sélectionner un attribut** étiquette. Cet attribut n'a aucun effet sur la règle, vous pouvez donc sélectionner n'importe quel attribut disponible.  
  
12. Dans le volet **Modifier la condition** , dans la zone **Groupe de suivi des modifications** , tapez le numéro du groupe de suivi des modifications que vous avez attribué comme l’un des composants requis.  
  
13. Dans le volet **Modifier la condition** , cliquez sur **Enregistrer l’élément**.  
  
14. Dans le volet **Composants** , développez le nœud **Actions** .  
  
15. Cliquez sur une action et faites-la glisser vers l’étiquette **Action** du volet **THEN** .  
  
16. Dans le volet **Attributs** , cliquez sur un attribut et faites-le glisser vers l’étiquette **Sélectionner un attribut** du volet **Modifier l’action** .  
  
17. Dans le volet **Modifier l’action** , remplissez tous les champs obligatoires.  
  
18. Dans le volet **Modifier l’action** , cliquez sur **Enregistrer l’élément**.  
  
19. Cliquez sur **Précédent**.  
  
20. (Facultatif) Dans la page **Maintenance des règles d’entreprise** , sur la ligne qui contient votre règle d’entreprise, double-cliquez sur une cellule dans la colonne **Nom**, **Description**ou **Notification** pour mettre à jour la valeur.  
  
    > [!NOTE]  
    >  Des notifications sont envoyées uniquement pour les règles qui incluent une action de validation.  
  
21. Cliquez sur **Publier les règles d’entreprise**.  
  
22. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. L’état de la règle devient **Actif**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles métier &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une Version par rapport aux règles métier &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)   
 [Les règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
