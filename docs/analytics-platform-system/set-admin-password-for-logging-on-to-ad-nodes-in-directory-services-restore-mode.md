---
title: Définir de mot de passe Active Directory - Analytique Platform System | Microsoft Docs
description: Définir le mot de passe d’ouverture de session Active Directory nœuds administrateur en Mode restauration des Services d’annuaire dans Analytique Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3df6203a4d98bace5d23a92e70a596a34dedb60e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678344"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Définir le mot de passe administrateur pour ouvrir une session sur les nœuds AD dans les Services d’annuaire de restauration en Mode (DSRM) - système de plateforme d’Analytique
Mode de restauration des Services annuaire (DSRM) est un mode de démarrage pour réparer ou de récupérer les Services de domaine Active Directory (AD DS). Il est utilisé pour se connecter aux nœuds d’appliance AD une fois que les services AD DS a échoué ou lorsque les services AD DS doit être restaurée. Le mot de passe DSRM a été initialisé lors de l’installation de l’appliance sur le site de fournisseur de matériel et doit être modifié par l’administrateur de l’appliance. Analytique Platform System a deux AD DS (contrôleurs de domaine) ;  **_appliance_domain_-AD01** et  **_appliance_domain_-AD02**. Pour chaque nœud de l’appliance AD, modifiez le mot de passe DSRM en procédant comme suit.  
  
## <a name="HowToDSRM"></a>Pour réinitialiser le mot de passe administrateur  
  
1.  Ouvrez une fenêtre d’invite de commandes sur un nœud d’appliance AD  <strong>_appliance_domain_-AD_xx_</strong>machine virtuelle.  
  
2.  À l’invite de commandes, tapez `ntdsutil`.  
  
3.  À la **ntdsutil** invite, tapez `set dsrm password`.  
  
4.  À la **réinitialiser le mot de passe administrateur :** invite, tapez `reset password on server null`.  
  
5.  À l’invite, tapez le nouveau mot de passe.  
  
6.  Répétez les étapes 1 à 5 ci-dessus pour chaque machine virtuelle de l’appliance AD.  
  
    > [!WARNING]  
    > Analytique Platform System ne prend pas en charge le caractère de signe dollar ($) dans l’administrateur de domaine ou les mots de passe d’administrateur local. Un mot de passe contenant un signe dollar validera et être utilisable mais peut bloquer les activités de mise à niveau et de maintenance.  
  
> [!NOTE]  
> Si les Services de domaine Active Directory ou de la machine virtuelle est endommagée pour une machine virtuelle de AD spécifique, en cours d’exécution **ReplaceVM** pour la publicité affectée machine virtuelle est l’action corrective recommandée. CSS contact pour obtenir une assistance.  
  
## <a name="see-also"></a>Voir aussi  
[Réinitialisation de mot de passe &#40;Analytique Platform System&#41;](password-reset.md)  
  
