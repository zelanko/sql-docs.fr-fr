---
title: 'Nouvelle attribution de rôle système : Modifier la Page attributions de rôle système (Gestionnaire de rapports) | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 4cc3521561aac3e91e2af2dd8f45eea77b74b58e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142632"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a>Page Nouvelle attribution de rôle système : Modifier les attributions de rôles système (Gestionnaire de rapports)
  La page Nouvelle attribution de rôle système ou Modifier les attributions de rôle système vous permet de définir la sécurité pour le serveur de rapports. La sécurité est définie par l'intermédiaire des attributions de rôle qui mappent des groupes ou des utilisateurs spécifiques aux tâches qu'ils peuvent effectuer. La liste des tâches est représentée sous la forme d'une définition de rôle que vous sélectionnez lors de l'attribution de rôle.  
  
 Au niveau système, les attributions de rôle que vous créez ou modifiez s'appliquent à l'ensemble du serveur de rapports. Par exemple, la possibilité de créer des planifications partagées est spécifiée au niveau système, car celles-ci sont utilisées par tout le système.  
  
 Par défaut, Reporting Services fournit deux rôles de niveau système prédéfinis :  
  
-   L'utilisateur système inclut des tâches qui permettent aux utilisateurs de consulter des propriétés de serveur de rapports et des planifications partagées, ainsi que d'exécuter des définitions de rapport, qui permettent aux utilisateurs de consulter des rapports générés interactifs publiés sur le serveur de rapports. La plupart des utilisateurs doivent être assignés à ce rôle.  
  
-   Administrateur système inclut des tâches pour créer et gérer des planifications partagées, définir des propriétés de serveur et créer des attributions de rôles au niveau du système pour d'autres utilisateurs. Peu d'utilisateurs ont besoin d'autorisations à ce niveau.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a>Pour ouvrir la page Nouvelle attribution de rôle système ou Modifier les attributions de rôles système  
  
1.  Ouvrez le Gestionnaire de rapports.  
  
2.  En haut de la page, dans l'angle droit, cliquez sur **Paramètres du site**. La page des propriétés générales du site s'ouvre.  
  
3.  Sélectionnez l'onglet **Sécurité** . Vous devez disposer des autorisations de gestionnaire de contenu et d'administrateur système pour accéder à cette page.  
  
4.  Pour créer une attribution de rôle, cliquez sur **Nouvelle attribution de rôle** dans la barre d'outils. Pour modifier une attribution de rôle existante, cliquez sur **Modifier** en regard d'un groupe ou utilisateur dans la page de propriétés Sécurité.  
  
## <a name="options"></a>Options  
 **Groupe ou utilisateur**  
 Tapez le nom d'un compte d'utilisateur ou de groupe dans votre domaine. Si le serveur de rapports s'exécute sous un compte local, vous devez spécifier les utilisateurs ou les groupes locaux. S'il s'exécute sous un compte de domaine, vous devez spécifier les utilisateurs ou les groupes de domaine. Entrez le compte sous ce format : \<domaine >\\< compte\>.  
  
> [!NOTE]  
>  Cette case est disponible uniquement dans la page Nouvelle attribution de rôle.  
  
 **Roles**  
 Fournit une liste de rôles au niveau du système que vous pouvez attribuer à d'autres utilisateurs. Vous pouvez spécifier plusieurs rôles pour une attribution de rôle unique.  
  
 Le Gestionnaire de rapports n'affiche pas les tâches dans chaque rôle ni ne propose de façon d'ajouter ou de modifier les tâches. Vous devez utiliser les rôles comme ils sont définis. Pour créer, modifier, ou supprimer des rôles, utilisez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
 Notez que si vous utilisez [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services, vous devez utiliser les rôles par défaut qui sont fournies.  
  
 **Descriptions**  
 Affiche des informations supplémentaires sur le rôle. Pour les rôles prédéfinis, tels que Utilisateur système ou Administrateur système, la description résume les tâches que chaque rôle prend en charge.  
  
 **Supprimer l’attribution de rôle**  
 Cliquez pour supprimer une attribution de rôle existante pour un utilisateur ou un groupe. Vous ne pouvez pas supprimer une attribution de rôle s'il s'agit de la dernière (chaque élément doit posséder une attribution de rôle au minimum).  
  
> [!NOTE]  
>  Ce bouton est disponible uniquement dans la page Modifier l'attribution de rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Attributions de rôles](security/role-assignments.md)   
 [Définitions de rôles](security/role-definitions.md)  
  
  