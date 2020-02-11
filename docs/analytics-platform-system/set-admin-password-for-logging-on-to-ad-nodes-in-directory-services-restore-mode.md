---
title: Définir le mot de passe Active Directory
description: Définissez Active Directory nœuds mot de passe de connexion administrateur en mode restauration des services d’annuaire dans Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbbf42106602a25b03072a9c9abfb04f04d3c49
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400337"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Définir le mot de passe d’administrateur pour la connexion aux nœuds AD en mode de restauration des services d’annuaire (DSRM)-Analytics Platform System
Le mode de restauration des services d’annuaire (DSRM) est un mode de démarrage pour la réparation ou la récupération de Active Directory Domain Services (AD DS). Il est utilisé pour se connecter aux nœuds AD de l’appliance après l’échec de AD DS ou lorsque AD DS doit être restauré. Le mot de passe pour DSRM a été initialisé lors de la configuration de l’appliance sur le site du fournisseur de matériel et doit être modifié par l’administrateur de l’appliance. Analytics Platform System a deux AD DS (contrôleurs de domaine); ** _appliance_domain_-ad01** et ** _appliance_domain_-AD02**. Pour chaque nœud AD d’appliance, modifiez le mot de passe DSRM en procédant comme suit.  
  
## <a name="HowToDSRM"></a>Pour réinitialiser le mot de passe de l’administrateur  
  
1.  Ouvrez une fenêtre d’invite de commandes sur un nœud AD d’appliance <strong> _appliance_domain_AD_xx_</strong>machine virtuelle.  
  
2.  Dans l’invite de commandes, tapez `ntdsutil`.  
  
3.  À l’invite **Ntdsutil** , tapez `set dsrm password`.  
  
4.  À l’invite de **réinitialisation du mot de passe administrateur :** , tapez `reset password on server null`.  
  
5.  À l’invite, tapez le nouveau mot de passe.  
  
6.  Répétez les étapes 1-5 ci-dessus pour chaque machine virtuelle AD d’appliance.  
  
    > [!WARNING]  
    > Analytics Platform System ne prend pas en charge le caractère de signe dollar ($) dans les mots de passe d’administrateur de domaine ou d’administrateur local. Un mot de passe contenant un signe dollar est validé et utilisable, mais peut bloquer les activités de mise à niveau et de maintenance.  
  
> [!NOTE]  
> Si la Active Directory Domain Services ou la machine virtuelle est endommagée pour une machine virtuelle Active Directory spécifique, l’exécution de **ReplaceVM** pour la machine virtuelle Active Directory affectée est l’action corrective recommandée. Contactez le code CSS pour obtenir de l’aide.  
  
## <a name="see-also"></a>Voir aussi  
[Réinitialisation du mot de passe &#40;Analytics Platform System&#41;](password-reset.md)  
  
