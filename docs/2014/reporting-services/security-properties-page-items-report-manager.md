---
title: Page de propriétés de sécurité, éléments (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 351b8503-354f-4b1b-a7ac-f1245d978da0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb1835a67ca1f909bf382fd227783cb0a20bbbf5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025727"
---
# <a name="security-properties-page-items-report-manager"></a>Page Propriétés de sécurité, Éléments (Gestionnaire de rapports)
  La page Propriétés de sécurité vous permet d'afficher ou de modifier les paramètres de sécurité qui déterminent l'accès aux dossiers, aux rapports, aux modèles, aux ressources et aux sources de données partagées. Cette page est disponible pour les éléments que vous êtes autorisé à sécuriser.  
  
 L'accès aux éléments est défini par l'intermédiaire des attributions de rôle qui spécifient les tâches que peuvent effectuer un groupe ou un utilisateur. Une attribution de rôle est composée d'un nom d'utilisateur ou de groupe et d'une ou plusieurs définitions de rôles qui spécifient une collection de tâches.  
  
 Les paramètres de sécurité sont transmis du dossier racine aux sous-dossiers et aux éléments contenus dans ces dossiers. Si vous n'arrêtez pas de façon explicite la sécurité héritée, les sous-dossiers et les éléments héritent du contexte de sécurité d'un élément parent. Si vous redéfinissez une stratégie de sécurité pour un dossier situé au milieu de la hiérarchie, tous ses éléments enfants (y compris les sous-dossiers) utiliseront les nouveaux paramètres de sécurité.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-security-page-for-an-item"></a>Pour ouvrir la page Sécurité pour un élément  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez l'élément pour lequel vous souhaitez configurer des paramètres de sécurité.  
  
2.  Pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, effectuez l'une des étapes suivantes :  
  
    -   Cliquez sur **Sécurité**. La page de propriétés de sécurité s'ouvre pour l'élément.  
  
    -   Cliquez sur **Gérer** pour ouvrir la page des propriétés générales pour l'élément. Sélectionnez ensuite l'onglet **Sécurité** .  
  
 **Modifier la sécurité de l'élément**  
 Cliquez pour modifier la définition de la sécurité pour l'élément actif. Si vous modifiez la sécurité d'un dossier, vos modifications s'appliquent au contenu du dossier actif et des sous-dossiers.  
  
 Ce bouton n'est pas disponible pour le dossier racine.  
  
 Les boutons ci-dessous deviennent disponibles lorsque vous modifiez la sécurité d'un élément.  
  
 **Supprimer**  
 Activez la case à cocher en regard du nom d'utilisateur ou de groupe à supprimer et cliquez sur **Supprimer**. Vous ne pouvez pas supprimer une attribution de rôle s'il s'agit de la dernière ou s'il s'agit d'une attribution de rôle intégrée (par exemple « Built-in\Administrateurs ») qui définit la ligne de base de la sécurité du serveur de rapports. La suppression d'une attribution de rôle n'entraîne pas celle d'un compte d'utilisateur ou de groupe ou des définitions de rôles.  
  
 **Nouvelle attribution de rôle**  
 Cliquez pour ouvrir la page Nouvelle attribution de rôle qui permet de créer des attributions de rôles supplémentaires pour l'élément actif. Pour plus d’informations, consultez [nouvelle attribution de rôle : Page Modifier le rôle attribution &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md).  
  
 **Rétablir la sécurité du Parent**  
 Cliquez pour rétablir les paramètres de sécurité en fonction de ceux du dossier immédiatement parent. Si l'héritage est arrêté dans toute l'arborescence des dossiers du serveur de rapports, les paramètres de sécurité du dossier de niveau supérieur (Dossier racine) sont utilisés.  
  
 **Groupe ou utilisateur**  
 Répertorie les groupes et les utilisateurs qui font partie de l'attribution de rôle existante pour l'élément actuel. Les attributions de rôle existantes pour le dossier actif sont définies pour les groupes et les utilisateurs qui apparaissent dans cette colonne. Vous pouvez cliquer sur un nom d'utilisateur ou de groupe pour afficher ou modifier les détails d'une attribution de rôle.  
  
 **Roles**  
 Répertorie une ou plusieurs définitions de rôles qui font partie d'une attribution de rôle existante. Si plusieurs rôles sont attribués à un compte d'utilisateur ou de groupe, ce groupe ou cet utilisateur peut effectuer toutes les tâches qui appartiennent à ces rôles. Pour afficher les tâches associées à un rôle, utilisez SQL Server Management Studio pour consulter les tâches dans chaque définition de rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Rôles prédéfinis](security/role-definitions-predefined-roles.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Attributions de rôles](security/role-assignments.md)   
 [Définitions de rôles](security/role-definitions.md)  
  
  
