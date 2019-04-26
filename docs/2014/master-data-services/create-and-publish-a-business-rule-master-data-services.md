---
title: Créer et publier une règle d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 65670b6958d2b0de36d1771d8c85bacfed1fa9a3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765792"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a>Créer et publier une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une règle d'entreprise pour garantir l'exactitude de vos données de référence. Après avoir créé une règle, vous devez la publier avant de pouvoir l'appliquer aux données.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-and-publish-a-business-rule"></a>Pour créer et publier une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **Type de membre** , sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Cliquez sur **Ajouter une règle d’entreprise**.  
  
8.  Cliquez sur **Modifier la règle d’entreprise sélectionnée**.  
  
9. Dans le volet **Composants** , développez le nœud **Conditions** .  
  
10. Cliquez sur une condition et faites-la glisser vers le **IF** du volet **Conditions** étiquette.  
  
    > [!TIP]  
    >  Vous pouvez supprimer des éléments de votre règle d’entreprise en effectuant un clic droit et en choisissant **supprimer**.  
  
11. Dans le **attributs** volet, cliquez sur un attribut et faites-le glisser vers le **modifier la Condition** du volet **sélectionner un attribut** étiquette.  
  
12. Dans le **modifier la Condition** volet, remplissez tous les champs requis.  
  
13. Dans le volet **Modifier la condition** , cliquez sur **Enregistrer l’élément**.  
  
14. Dans le volet **Composants** , développez le nœud **Actions** .  
  
15. Cliquez sur une action et faites-la glisser vers l’étiquette **Action** du volet **THEN** .  
  
16. Dans le volet **Attributs** , cliquez sur un attribut et faites-le glisser vers l’étiquette **Sélectionner un attribut** du volet **Modifier l’action** .  
  
17. Dans le volet **Modifier l’action** , remplissez tous les champs obligatoires.  
  
18. Dans le volet **Modifier l’action** , cliquez sur **Enregistrer l’élément**.  
  
19. Éventuellement, ajoutez plusieurs conditions à la règle. Pour plus d’informations, consultez [Ajouter plusieurs conditions à une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).  
  
20. Cliquez sur **Précédent**.  
  
21. (Facultatif) Dans la page **Maintenance des règles d’entreprise** , sur la ligne qui contient votre règle d’entreprise, double-cliquez sur une cellule dans la colonne **Nom**, **Description**ou **Notification** pour mettre à jour la valeur.  
  
    > [!NOTE]  
    >  Des notifications sont envoyées uniquement pour les règles qui incluent une action de validation.  
  
22. Cliquez sur **Publier les règles d’entreprise**.  
  
23. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. L’état de la règle devient **Actif**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)   
 [Modifier le nom d’une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Ajouter plusieurs conditions à une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
