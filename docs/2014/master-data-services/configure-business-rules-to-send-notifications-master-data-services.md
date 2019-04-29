---
title: Configurer des règles d’entreprise pour envoyer des notifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 05ca904445d4a13cdf957ed82e70c70d57b3ad17
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925572"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a>Configurer des règles d'entreprise pour envoyer des notifications (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configurez des règles d'entreprise pour envoyer des notifications lorsque vous souhaitez informer les utilisateurs des modifications apportées aux valeurs d'attribut.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder aux zones fonctionnelles **Administration de système** et **Autorisations d'accès** . Si vous n'avez pas d'autorisation sur la zone fonctionnelle **Autorisations d'accès** , vous ne pouvez pas afficher la liste des utilisateurs et groupes auxquels envoyer des notifications.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Une règle d'entreprise qui utilise une action de validation doit déjà exister. Pour plus d’informations, consultez [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
-   L’utilisateur ou le groupe qui reçoit la notification doit avoir au moins l’autorisation **Lecture seule** sur l’attribut qui n’a pas été validé. Les utilisateurs ou les groupes qui se voient refuser explicitement ou implicitement l'autorisation à l'attribut recevront le courrier électronique, mais ne seront pas en mesure d'accéder à l'attribut dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Si un courrier électronique est envoyé à un groupe, seuls les membres du groupe qui ont accédé à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] le recevront.  
  
### <a name="to-configure-business-rules-to-send-notifications"></a>Pour configurer des règles d'entreprise pour envoyer des notifications  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  À partir de la **Type de membre** , sélectionnez un type de membre.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Dans la grille, dans la ligne de la règle d’entreprise, double-cliquez sur le **Notification** champ.  
  
8.  Dans le sous-menu, cliquez sur un utilisateur ou un groupe pour envoyer la notification par e-mail.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   Configurez le protocole de messagerie comme suit :  
  
    -   [Configurer des notifications par e-mail &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)   
 [Configurer des notifications par e-mail &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
