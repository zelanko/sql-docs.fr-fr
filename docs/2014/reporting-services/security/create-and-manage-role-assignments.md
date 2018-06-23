---
title: Créer et gérer des attributions de rôles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- security [Reporting Services], role assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 4d31a978b4b668045a14f2bf9dbbcaf0317b3c5d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042384"
---
# <a name="create-and-manage-role-assignments"></a>Créer et gérer des attributions de rôles
  Une *attribution de rôle* est une stratégie de sécurité qui détermine si un utilisateur ou un groupe peut accéder à un élément de serveur de rapports spécifique ou effectuer une opération. Elle se compose d'un seul nom de compte d'utilisateur ou de groupe et d'une ou de plusieurs définitions de rôles.  
  
 Les attributions de rôles ont comme portée le *niveau élément* ou le *niveau système*.  
  
-   Une attribution de rôle au niveau élément est toujours créée dans le contexte d'un élément ou d'une branche spécifique de l'arborescence des dossiers du serveur de rapports. Vous naviguez jusqu'à un dossier ou un élément spécifique pour lui créer une attribution de rôle.  
  
-   Les attributions de rôles au niveau système permettent aux utilisateurs sélectionnés d'effectuer des tâches qui affectent le site du serveur de rapports dans son ensemble. Ces tâches comprennent la création de planifications partagées, la gestion de travaux, le traitement des rapports dans le Générateur de rapports et la définition de propriétés. La sécurité au niveau système n'implique pas d'accès aux éléments de l'arborescence des dossiers du serveur de rapports.  
  
## <a name="creating-an-item-level-role-assignment"></a>Création d'une attribution de rôle au niveau élément  
 Pour créer ou gérer des attributions de rôles, utilisez le Gestionnaire de rapports et ouvrez les pages de propriétés Sécurité de l'élément que vous voulez sécuriser.  
  
 Vous devez créer une attribution de rôle distincte pour chaque compte d'utilisateur ou de groupe qui requiert un accès au serveur de rapports. Si le compte se trouve sur un domaine autre que celui qui contient le serveur de rapports, incluez le nom de domaine. Après avoir spécifié un compte, vous pouvez choisir une ou plusieurs définitions de rôles. Les définitions de rôles s'additionnent. L'ensemble combiné de toutes les tâches de toutes les définitions est pris en charge dans l'attribution relative à un utilisateur ou à un groupe spécifique.  
  
 Pour activer un accès largement ouvert, vous pouvez choisir un élément qui est élevé dans la hiérarchie de dossiers (par exemple, le Dossier racine du nœud racine). Vous pouvez ensuite créer des attributions de rôles pour verrouiller différentes zones spécifiques dans la hiérarchie de dossiers.  
  
 Vous devez être membre du groupe local Administrateurs sur l'ordinateur serveur de rapports pour créer une attribution de rôle. Vous pouvez déléguer cette responsabilité en affectant d’autres utilisateurs au rôle **Gestionnaire de contenu** .  
  
 Pour plus d’informations, consultez [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).  
  
## <a name="creating-a-system-level-role-assignment"></a>Création d'une attribution de rôle au niveau système  
 Pour créer ou gérer une attribution de rôle au niveau système, utilisez le Gestionnaire de rapports et ouvrez la page Paramètres du site.  
  
 Les attributions de rôles au niveau système et au niveau élément sont compatibles. Vous devez créer une attribution de rôle au niveau système pour chaque utilisateur ou groupe qui a une attribution de rôle au niveau élément.  
  
 Les attributions de rôles au niveau système incluent un large éventail d'autorisations, mais elles n'incluent pas les autorisations qui font partie d'une attribution de rôle au niveau élément. Contrairement aux autorisations système sur un ordinateur, les rôles système dans les serveurs de rapports n'acheminent pas des autorisations primordiales qui incluent le jeu complet de toutes les opérations possibles. Au lieu de cela, les attributions de rôles au niveau système sont simplement un ensemble des tâches dont la portée est le site du serveur de rapports. Les autorisations acheminées par le biais d'attributions de rôles système déterminent si les utilisateurs peuvent afficher les propriétés des applications (telles que l'image ou le titre de la page d'accueil), afficher ou gérer des planifications partagées, ou utiliser le Générateur de rapports.  
  
 Pour plus d’informations, consultez [accorder l’accès utilisateur à un serveur de rapports &#40;le Gestionnaire de rapports&#41; ](grant-user-access-to-a-report-server.md) et [de rôles prédéfinis](role-definitions-predefined-roles.md).  
  
## <a name="modifying-a-role-assignment"></a>Modification d'une attribution de rôle  
 Vous pouvez modifier une attribution de rôle à tout moment. Vos modifications prennent effet lorsque vous enregistrez l'attribution de rôle. Les sessions utilisateur ne sont pas affectées par les modifications d'attributions de rôles. Si un utilisateur a un rapport ouvert, et que vous modifiez une attribution de rôle pour en refuser l'accès, l'utilisateur peut continuer à utiliser le rapport tant que la session est active.  
  
 Si vous ajoutez un compte d'utilisateur à un groupe qui fait déjà partie d'une attribution de rôle, un délai s'écoulera avant que le compte d'utilisateur puisse accéder aux éléments par le biais des stratégies de compte de groupe. Ce délai est dû à la mise en cache des jetons d'authentification par IIS (Internet Information Services). Vous pouvez attendre que les jetons soient actualisés (ce délai est généralement de quinze minutes) ou réinitialiser IIS pour mettre à jour le cache immédiatement.  
  
 Vous pouvez uniquement modifier une attribution de rôle à la fois. Vous ne pouvez pas effectuer d'opération de recherche et de remplacement globale afin de changer des noms de définition de rôle ou des paramètres d'attribution de rôle, ou de trouver toutes les attributions de rôles qui incluent un utilisateur ou un groupe spécifique.  
  
## <a name="deleting-a-role-assignment"></a>Suppression d'une attribution de rôle  
 Vous pouvez supprimer des attributions de rôles en cochant les cases en regard de chaque attribution que vous voulez supprimer, puis en cliquant sur **Supprimer**. Vous pouvez également supprimer des attributions de rôles en cliquant sur **Rétablir la sécurité parente**. Lorsque vous cliquez sur ce bouton, les attributions de rôles existantes pour l'élément sont supprimées, et celles qui proviennent d'un élément parent sont utilisées à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;](grant-user-access-to-a-report-server.md)   
 [Modifier ou supprimer une affectation de rôle &#40;Gestionnaire de rapports&#41;](role-assignments-modify-or-delete.md)   
 [Attributions de rôles](role-assignments.md)   
 [Définitions de rôles](role-definitions.md)   
 [Rôles prédéfinis](role-definitions-predefined-roles.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](granting-permissions-on-a-native-mode-report-server.md)  
  
  