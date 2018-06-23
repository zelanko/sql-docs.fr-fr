---
title: Page Sécurité (Paramètres du site. Gestionnaire de rapports) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: b4115675e8f9529873eeeec5f71d2b5861fef9eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151826"
---
# <a name="security-page-site-settings-report-manager"></a>Page Sécurité (Paramètres du site. Gestionnaire de rapports)
  La page Sécurité vous permet d'afficher les attributions de rôles système qui contrôlent l'accès au site du serveur de rapports. Les attributions de rôle système existent en dehors de l'étendue de l'espace de noms ou de l'arborescence des dossiers du serveur de rapports. Ils sont globaux et ne peuvent pas être différents pour des éléments spécifiques. Les opérations prises en charge par le biais des attributions de rôles système incluent la création et l'utilisation des planifications partagées, l'utilisation du Générateur de rapports et la définition de valeurs par défaut pour certaines fonctionnalités de serveur.  
  
 Une attribution de rôle système par défaut est créée lors de l'installation du serveur de rapports. Cette attribution de rôles système accorde aux administrateurs du système local les autorisations nécessaires à la gestion de l'environnement du serveur de rapports. Un administrateur du système local peut toujours définir la sécurité d'un serveur de rapports local, même si les attributions de rôles système sont supprimées.  
  
 Tous les autres utilisateurs qui ont besoin d'accéder au Générateur de rapports ou aux planifications partagées doivent être assignés à une attribution de rôle système.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-security-page-for-site-settings"></a>Pour ouvrir la page Sécurité pour Paramètres du site  
  
1.  Ouvrez le Gestionnaire de rapports.  
  
2.  Cliquez sur **Paramètres du site**en haut de la page. La page des propriétés générales du site s'ouvre.  
  
3.  Sélectionnez l'onglet **Sécurité** .  
  
## <a name="options"></a>Options  
 **Supprimer**  
 Cliquez pour supprimer une attribution de rôle existante. Avant de cliquer sur ce bouton **Supprimer**, activez la case à cocher en regard du nom d'utilisateur ou de groupe que vous souhaitez supprimer. Vous ne pouvez pas supprimer une attribution de rôle s'il s'agit de la seule qui reste. La suppression d'une attribution de rôle n'entraîne pas celle d'un compte d'utilisateur ou de groupe ou des définitions de rôles.  
  
 **Nouvelle attribution de rôle**  
 Cliquez pour ouvrir la page Nouvelle attribution de rôle système qui permet de créer des attributions de rôles système supplémentaires pour le site du serveur de rapports. Pour plus d’informations, consultez [nouvelle attribution de rôle système : modifier la Page d’attributions de rôle système &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).  
  
 **Modifier**  
 Cliquez pour ouvrir la page Modifier les attributions de rôles système qui permet de modifier des attributions de rôles système individuelles pour le site du serveur de rapports. Pour plus d’informations, consultez [nouvelle attribution de rôle système : modifier la Page d’attributions de rôle système &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).  
  
 **Groupe ou utilisateur**  
 Répertorie les groupes et les utilisateurs qui font partie de l'attribution de rôle existante. Les attributions de rôle existantes pour le dossier actif sont définies pour les groupes et les utilisateurs qui apparaissent dans cette colonne. Cliquez sur **Modifier** en regard d'un nom d'utilisateur ou de groupe pour afficher ou modifier les détails d'une attribution de rôle.  
  
 **Roles**  
 Répertorie une ou plusieurs définitions de rôles qui font partie d'une attribution de rôle existante. Si plusieurs rôles sont attribués à un compte d'utilisateur ou de groupe, ce groupe ou cet utilisateur peut effectuer toutes les tâches qui appartiennent à tous les rôles. Pour afficher l’ensemble des tâches que chaque rôle prend en charge, utilisez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Vous ne pouvez pas afficher, créer, modifier ni supprimer des rôles dans le Gestionnaire de rapports. Pour obtenir des instructions, consultez [créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  