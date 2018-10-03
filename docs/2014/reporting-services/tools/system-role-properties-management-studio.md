---
title: Propriétés de rôle système (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cadf4ff8d9164de453671aeb3e49013ad04ce1de
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112689"
---
# <a name="system-role-properties-management-studio"></a>Propriétés de rôle système (Management Studio)
  La page Rôles système vous permet d'afficher les définitions de rôles système qui sont actuellement définies pour le serveur de rapports. Une définition de rôle système contient une collection nommée de tâches effectuées sur tout le site plutôt que sur un élément individuel. Les définitions de rôles sont attribuées à un utilisateur ou à des groupes pour créer une attribution de rôle. Les tâches contenues dans la définition de rôle spécifient les opérations que peuvent effectuer l'utilisateur ou le groupe.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a deux définitions de rôles système prédéfinies : **Administrateur système** et **Utilisateur système**. Vous pouvez les modifier en changeant la liste des tâches de chacune d'elles, ou vous pouvez créer un rôle système qui prend en charge une autre combinaison de tâches. La modification d'une définition de rôle affecte toutes les attributions de rôles qui contiennent la définition de rôle.  
  
> [!NOTE]  
>  Les attributions de rôles système sont utilisées uniquement sur un serveur de rapports qui s'exécute en mode natif. Si le serveur de rapports est configuré pour l'intégration SharePoint, cette page n'est pas disponible.  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifie le nom de la définition du rôle système.  
  
 **Description**  
 Affiche une description de la définition du rôle système. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], cette description n'est visible que sur cette page. Les utilisateurs qui consultent cet élément par le biais du Gestionnaire de rapports peuvent afficher cette description en parcourant l'arborescence des dossiers.  
  
 **Tâche**  
 Répertorie toutes les tâches au niveau système qui peuvent être sélectionnées pour la définition de ce rôle. Vous pouvez ajouter ou supprimer des éléments dans la liste des tâches prédéfinies pour spécifier comment les utilisateurs accèdent à un élément donné par le biais de ce rôle. Vous ne pouvez ni créer de nouvelles tâches, ni modifier les tâches existantes.  
  
 **Description**  
 Donne des informations sur chaque tâche. Vous ne pouvez pas modifier la description des tâches.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](report-server-in-management-studio-f1-help.md)   
 [Tâches au niveau système](../security/tasks-and-permissions-system-level-tasks.md)   
 [Tâches et autorisations](../security/tasks-and-permissions.md)   
 [Rôles prédéfinis](../security/role-definitions-predefined-roles.md)  
  
  
