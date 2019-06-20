---
title: 'Nouvelle attribution de rôle : Modifier la Page d’attribution de rôle (Gestionnaire de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3319ced0-4b86-42af-b18d-da41a625113c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9480b0729e7c08117ba5633c6934eca1903a61b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108154"
---
# <a name="new-role-assignment-edit-role-assignment-page-report-manager"></a>Nouvelle attribution de rôle : Modifier la Page d’attribution de rôle (Gestionnaire de rapports)
  Utilisez la page Nouvelle attribution de rôle ou Modifier l'attribution de rôle pour accorder des autorisations à des opérations et éléments de serveur de rapports. Chaque utilisateur qui demande l'accès à un serveur de rapports doit posséder une attribution de rôle qui définit le niveau d'accès. Vous pouvez créer des attributions de rôles au nœud racine ou sur un rapport, modèle, dossier, ressource ou source de données partagée spécifique. La sécurité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est mise en place via les attributions de rôle que vous appliquez aux éléments. Une attribution de rôle fait correspondre un groupe ou un utilisateur à une définition de rôle. Chaque définition de rôle identifie les tâches que les groupes ou les utilisateurs peuvent effectuer sur un élément spécifique.  
  
 Les attributions de rôle au niveau élément peuvent avoir un large impact. Bien qu'elles puissent être associées à un seul rapport ou dossier, elles peuvent être également définies à un haut niveau dans l'arborescence des dossiers et être héritées par des dossiers et des éléments situés à un niveau inférieur dans l'arborescence. Pour plus d’informations, consultez [accorder l’accès utilisateur à un serveur de rapports &#40;le Gestionnaire de rapports&#41;](security/grant-user-access-to-a-report-server.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-new-role-assignment-or-edit-role-assignment-page"></a>Pour ouvrir la page Nouvelle attribution de rôle ou Modifier l'attribution de rôle  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez un élément pour lequel vous souhaitez ajouter ou modifier une attribution de rôle.  
  
2.  Pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Sécurité**. La page de propriétés de sécurité s'ouvre pour l'élément.  
  
4.  Si vous souhaitez ajouter une nouvelle attribution de rôle, dans la barre d'outils, cliquez sur **Nouvelle attribution de rôle**. Si vous souhaitez apporter des modifications à une attribution de rôle, cliquez sur **Modifier** en regard du nom de l'utilisateur ou du groupe à modifier.  
  
    > [!NOTE]  
    >  Si un élément hérite actuellement de la sécurité de l'un de ses parents, cliquez sur **Modifier la sécurité de l'élément** dans la barre d'outils pour changer les paramètres de sécurité.  
  
## <a name="options"></a>Options  
 **Nom du groupe ou utilisateur**  
 Tapez le nom d'un compte d'utilisateur ou de groupe pour lequel l'attribution de rôle est créée. Ce nom d'utilisateur ou de groupe doit être un compte de domaine Windows valide. Entrez le compte sous ce format : \<domaine >\\< compte\>.  
  
> [!NOTE]  
>  Cette case est disponible uniquement dans la page Nouvelle attribution de rôle.  
  
 **Rôle**  
 Affiche tous les rôles définis sur le serveur de rapports qui permettent de définir la sécurité des éléments. Lorsque vous créez ou modifiez une attribution de rôle pour un rapport ou un dossier, sélectionnez un ou plusieurs rôles jusqu'à ce que l'ensemble combiné de tâches décrive les actions que l'utilisateur doit être autorisé à effectuer. Pour afficher l'ensemble des tâches que chaque rôle prend en charge, utilisez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Vous ne pouvez pas afficher, créer, modifier ni supprimer des rôles dans le Gestionnaire de rapports. Pour obtenir des instructions, consultez [créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
 **Description**  
 Affiche des informations supplémentaires sur le rôle. Pour les rôles prédéfinis, tels que **Navigateur** ou **Gestionnaire de contenu**, la description résume les tâches que chaque rôle prend en charge.  
  
 **Supprimer l’attribution de rôle**  
 Cliquez pour supprimer une attribution de rôle existante pour un utilisateur ou un groupe. Vous ne pouvez pas supprimer une attribution de rôle s'il s'agit de la dernière (chaque élément doit posséder une attribution de rôle au minimum).  
  
> [!NOTE]  
>  Ce bouton est disponible uniquement dans la page Modifier l'attribution de rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Attributions de rôles](security/role-assignments.md)   
 [Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;](security/grant-user-access-to-a-report-server.md)  
  
  
