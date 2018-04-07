---
title: Créer un administrateur de domaine APS (APS)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed52bf78-2b0a-4252-98a7-8c2805e22d3d
caps.latest.revision: 7
ms.openlocfilehash: 6842992931ba35f450d49d6db9beb803dce6b73a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="create-an-aps-domain-administrator"></a>Créer un administrateur de domaine APS
Certaines opérations requièrent des privilèges d’administrateur de domaine de système de plateforme Analytique. Cette rubrique explique comment créer des administrateurs de domaine de matériel supplémentaire.  
  
## <a name="create-a-domain-administrator"></a>Créer un administrateur de domaine  
Dispose des autorisations appropriées pour configurer tous les nœuds de points d’accès, l’utilisateur qui exécute le **Gestionnaire de Configuration de points d’accès** (`dwconfig.exe`) doit être un membre de la **Admins du domaine** groupe. Pour démarrer et arrêter les services de points d’accès, l’utilisateur doit être un membre de la **PdwControlNodeAccess** groupe.  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Pour ajouter un utilisateur au groupe Admins du domaine  
  
1.  Ouvrez une session sur le nœud actif AD **(*appliance_domain*-AD01** ou ***appliance_domain*-AD02**) à l’aide d’un compte d’administrateur de domaine appliance existant.  
  
2.  Dans le menu Démarrer, cliquez sur **Exécuter**. Dans le **ouvrir** , tapez **DSA.msc**. Cliquez sur **OK**.  
  
3.  Dans le **Active Directory Users and Computers** programme, avec le bouton droit **utilisateurs**, pointez sur **nouveau**, puis cliquez sur **utilisateur**.  
  
4.  Dans le **nouvel objet – utilisateur** boîte de dialogue, la description du nouvel utilisateur complète, puis cliquez sur **suivant**.  
  
    La boîte de dialogue mot de passe, puis cliquez sur **suivant**.  
  
    > [!WARNING]  
    > SQL Server PDW ne prend pas en charge le caractère de signe dollar ($) dans l’administrateur de domaine ou les mots de passe d’administrateur local. Un mot de passe qui contient un signe dollar est valide et utilisable, mais peut bloquer les activités de mise à niveau et de maintenance  
  
    Confirmer la nouvelle description de l’utilisateur, puis cliquez sur **Terminer**.  
  
5.  Dans la liste des utilisateurs, double-cliquez sur le nouvel utilisateur pour ouvrir la boîte de dialogue Propriétés.  
  
6.  Sur le **membre de** , cliquez sur **ajouter**.  
  
    Type **Admins du domaine ; PdwControlNodeAccess** puis cliquez sur **vérifier les noms**. Cliquez sur **OK**.  
  
    Cette opération ajoute le nouvel utilisateur à la **Admins du domaine** groupe et la **PdwControlNodeAccess** groupe. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40;Analytique plate-forme système&#41;](launch-the-configuration-manager.md)  
  
