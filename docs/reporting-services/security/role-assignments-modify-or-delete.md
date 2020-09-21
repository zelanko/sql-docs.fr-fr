---
description: Modifier ou supprimer une attribution de rôle (Portail web SSRS)
title: Modifier ou supprimer une attribution de rôle (portail web SSRS) | Microsoft Docs
ms.date: 05/07/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: defe3952f9fd3c5c4eb4453c2071820cb44a3fb8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480651"
---
# <a name="role-assignments---modify-or-delete"></a>Attributions de rôles - Modifier ou supprimer

Une attribution de rôle mappe un compte d’utilisateur ou de groupe à un rôle prédéfini qui définit les tâches qui peuvent être effectuées. Elle détermine les types de tâches qu’un utilisateur effectue sur un dossier, rapport, modèle ou autre type de contenu. Pour créer, modifier ou supprimer des attributions de rôles, vous devez utiliser le portail web SSRS. Après avoir créé une attribution de rôle pour un utilisateur ou un groupe particulier, vous pouvez la modifier ultérieurement en sélectionnant un autre rôle. Pour révoquer des autorisations d'accès à un serveur de rapports, vous pouvez supprimer une attribution de rôle du serveur de rapports.  

Selon votre objectif, d'autres approches peuvent être plus appropriées. Par exemple, vous pouvez personnaliser ou créer une définition de rôle, ou modifier l'appartenance (membership) d'un compte de groupe dans Active Directory.  

Par exemple, un groupe d’utilisateurs doit gérer son contenu, mais il ne doit pas disposer du jeu complet d’autorisations associé au Gestionnaire de contenu. Vous pouvez créer une définition de rôle appelée Gestionnaire de contenu de service. Elle peut inclure toutes les tâches du Gestionnaire de contenu, sauf **Définir des stratégies de sécurité pour les éléments**.

De même, si vous êtes administrateur système ou réseau, il vous est probablement plus facile de gérer les comptes de groupes Active Directory que les attributions de rôles dans le portail web. Vous pouvez réduire la surcharge liée à la gestion des attributions de rôles en créant une attribution de rôle unique pour un compte de groupe. Vous pouvez ensuite modifier l’appartenance au groupe quand les utilisateurs n’ont plus besoin d’accéder aux rapports.
  
 Si vous déterminez que la modification ou la suppression d’une attribution de rôle est la meilleure approche, n’oubliez pas de vérifier les attributions de rôles système et les attributions de rôles au niveau élément. Chaque type d’attribution de rôle est configuré par le biais de pages distinctes dans le portail web.
  
## <a name="to-modify-or-delete-a-system-role-assignment"></a>Pour modifier ou supprimer une attribution de rôle système
  
1. Accédez au [portail web d’un serveur de rapports &#40;Mode natif SSRS&#41;](../../reporting-services/web-portal-ssrs-native-mode.md).

2. Sélectionnez **Paramètres du site** > **Sécurité**. Toutes les attributions de rôles de niveau système définies actuellement pour le serveur ou le déploiement avec montée en puissance parallèle sont répertoriées par nom de compte.

3. Recherchez l'attribution de rôle à modifier ou à supprimer.

4. Pour ajouter ou supprimer le rôle d’un utilisateur ou d’un groupe particulier, sélectionnez **Modifier**.

5. Pour supprimer une attribution de rôle, cochez la case à côté du nom d’utilisateur ou de groupe, puis sélectionnez **Supprimer**.

### <a name="to-modify-or-delete-an-item-role-assignment"></a>Pour modifier ou supprimer une attribution de rôle au niveau élément

1. Accédez au portail web et recherchez l’élément pour lequel vous souhaitez modifier ou supprimer une attribution de rôle.

2. Pointez sur l’élément et sélectionnez la flèche déroulante.

3. Dans le menu déroulant, sélectionnez **Sécurité**.

4. Recherchez l'attribution de rôle à modifier ou à supprimer.

5. Pour ajouter ou supprimer le rôle d’un utilisateur ou d’un groupe particulier, sélectionnez **Modifier**.

6. Pour supprimer une attribution de rôle, cochez la case à côté du nom d’utilisateur ou de groupe, puis sélectionnez **Supprimer**.

## <a name="see-also"></a>Voir aussi

[Créer et gérer des attributions de rôles](../../reporting-services/security/create-and-manage-role-assignments.md)  
[Attributions de rôles](../../reporting-services/security/role-assignments.md)  
