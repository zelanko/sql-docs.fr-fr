---
title: "Définir le mot de passe d’ouverture de session administrateur AD nœuds en Mode restauration des Services Directory (APS)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97a9c715-2763-417d-b45c-bb0180759e47
caps.latest.revision: "20"
ms.openlocfilehash: 1496e3e18bde0fbe1daad452081191bbe0ffb23e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm"></a>Définir le mot de passe administrateur pour ouvrir une session sur les nœuds AD dans le Mode restauration Services d’annuaire (DSRM)
Mode de restauration des Services annuaire (DSRM) est un mode de démarrage pour réparer ou de récupérer les Services de domaine Active Directory (AD DS). Il est utilisé pour se connecter aux nœuds DISPOSITIF AD une fois les services AD DS a échoué ou lorsque les services AD DS doit être restaurée. Le mot de passe DSRM a été initialisée lors de l’installation de l’application sur le site de fournisseur de matériel et doit être modifié par l’administrateur de matériel. Système de plateforme Analytique a deux services AD DS (contrôleurs de domaine) ;  ***appliance_domain*-AD01** et  ***appliance_domain*-AD02**. Pour chaque nœud DISPOSITIF AD, modifiez le mot de passe DSRM en procédant comme suit.  
  
## <a name="HowToDSRM"></a>Pour réinitialiser le mot de passe administrateur  
  
1.  Ouvrez une fenêtre d’invite de commandes sur un nœud d’application AD   ***appliance_domain*AD*xx*** machine virtuelle.  
  
2.  À l’invite de commandes, tapez `ntdsutil`.  
  
3.  À la **ntdsutil** tapez `set dsrm password`.  
  
4.  À la **réinitialiser le mot de passe administrateur :** tapez `reset password on server null`.  
  
5.  À l’invite, tapez le nouveau mot de passe.  
  
6.  Répétez les étapes 1 à 5 ci-dessus pour chaque ordinateur virtuel de l’application AD.  
  
    > [!WARNING]  
    > Système de plateforme d’Analytique ne prend pas en charge le signe dollar ($) dans l’administrateur de domaine ou les mots de passe d’administrateur local. Un mot de passe qui contient un signe dollar valide et être utilisable mais peut bloquer les activités de mise à niveau et de maintenance.  
  
> [!NOTE]  
> Si les Services de domaine Active Directory ou de l’ordinateur virtuel est endommagé pour un ordinateur Active Directory spécifique, en cours d’exécution **ReplaceVM** pour Active Directory affecté machine virtuelle est l’action corrective recommandée. CSS contacter pour obtenir une assistance.  
  
## <a name="see-also"></a>Voir aussi  
[Réinitialisation du mot de passe &#40; Système de plateforme Analytique &#41;](password-reset.md)  
  
