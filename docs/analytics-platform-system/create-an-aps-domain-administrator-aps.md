---
title: Créer un administrateur de domaine
description: Certaines opérations requièrent des privilèges d’administrateur de domaine du système de plateforme d’analyse. Cela explique comment créer des administrateurs de domaine d’appliance supplémentaires.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 1a0d50e485f0e8f48de11b2e5a3c27c9f9be047e
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401232"
---
# <a name="create-an-aps-domain-administrator"></a>Créer un administrateur de domaine APS
Certaines opérations requièrent des privilèges d’administrateur de domaine du système de plateforme d’analyse. Cela explique comment créer des administrateurs de domaine d’appliance supplémentaires.  
  
## <a name="create-a-domain-administrator"></a>Créer un administrateur de domaine  
Pour disposer des autorisations suffisantes pour configurer tous les nœuds APS, l’utilisateur qui`dwconfig.exe`exécute l' **APS Configuration Manager** () doit être membre du groupe **Admins du domaine** . Pour démarrer et arrêter les services APS, l’utilisateur doit être membre du groupe **PdwControlNodeAccess** .  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Pour ajouter un utilisateur au groupe Admins du domaine  
  
1.  Connectez-vous au nœud AD actif **(_domaine d’appliance\__-ad01** ou domaine d' ** _Appliance\__-AD02**) à l’aide d’un compte d’administrateur de domaine d’appliance existant.  
  
2.  Dans le menu Démarrer, cliquez sur **Exécuter**. Dans la zone **ouvrir** , tapez **DSA. msc**. Cliquez sur **OK**.  
  
3.  Dans le programme **Active Directory les utilisateurs et les ordinateurs** , cliquez avec le bouton droit sur **utilisateurs**, pointez sur **nouveau**, puis cliquez sur **utilisateur**.  
  
4.  Dans la boîte de dialogue **nouvel objet-utilisateur** , complétez la description du nouvel utilisateur, puis cliquez sur **suivant**.  
  
    Renseignez la boîte de dialogue mot de passe, puis cliquez sur **suivant**.  
  
    > [!WARNING]  
    > SQL Server PDW ne prend pas en charge le signe dollar ($) dans les mots de passe d’administrateur de domaine ou d’administrateur local. Un mot de passe contenant un signe dollar est valide et utilisable, mais peut bloquer les activités de mise à niveau et de maintenance.  
  
    Confirmez la description du nouvel utilisateur, puis cliquez sur **Terminer**.  
  
5.  Dans la liste des utilisateurs, double-cliquez sur le nouvel utilisateur pour ouvrir la boîte de dialogue Propriétés de l’utilisateur.  
  
6.  Sous l’onglet **Membres de**, cliquez sur **Ajouter**.  
  
    Tapez **Admins du domaine ; PdwControlNodeAccess** , puis cliquez sur **vérifier les noms**. Cliquez sur **OK**.  
  
    Cela ajoute le nouvel utilisateur au groupe **Admins du domaine** et au groupe **PdwControlNodeAccess** . Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le système de plateforme Configuration Manager &#40;Analytics&#41;](launch-the-configuration-manager.md)  
  
