---
title: Boîte de dialogue Ajouter une adresse IP (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68bd85258bd3fd259386f020394ffb5bc70a9781
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164669"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a>Boîte de dialogue Ajouter une adresse IP (SQL Server Management Studio)
  Cette rubrique d'aide F1 décrit les options de la boîte de dialogue **Ajouter une adresse IP** . Cette boîte de dialogue accessible depuis la boîte de dialogue **Nouvel écouteur du groupe de disponibilité** et l'onglet **Écouteur** de la page **Spécifier les réplicas** de l' [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] ou l' [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer à ajouter des sous-réseaux à un écouteur de groupe de disponibilité, vérifiez que vous connaissez l'adresse IP de chaque sous-réseau et, pour une adresse IPv4, le masque de sous-réseau.  
  
##  <a name="PageOptions"></a> Options Ajouter une adresse IP  
 **Sous-réseau**  
 Utilisez la liste déroulante pour sélectionner une adresse pour le sous-réseau que vous ajoutez à l'écouteur du groupe de disponibilité. Par défaut, un sous-réseau possède une adresse IPv4 et une adresse IPv6. La première fois que vous utilisez la boîte de dialogue **Ajouter une adresse IP** , la liste déroulante **Sous-réseau** affiche les deux adresses de sous-réseau pour chaque sous-réseau qui héberge un réplica pour le groupe de disponibilité. Pour ajouter un sous-réseau donné à l'écouteur, sélectionnez l'une de ses adresses de sous-réseau.  
  
 Après avoir complété la boîte de dialogue **Ajouter une adresse IP** et cliqué sur **OK** pour ajouter une adresse de sous-réseau sélectionnée à l'écouteur, la liste déroulante **Sous-réseau** filtre cette adresse de sous-réseau. Toutes les adresses de sous-réseau non sélectionnées demeurent dans la liste déroulante. Assurez-vous que vous ajoutez une et une seule adresse de sous-réseau par sous-réseau à l'écouteur, sinon la création de l'écouteur échoue.  
  
 **Adresses**  
 Utilisez ce champ pour entrer une adresse IP statique pour l'adresse de sous-réseau sélectionnée. Contactez l'administrateur réseau pour connaître cette adresse IP. Assurez-vous que vous entrez une adresse valide pour l'adresse de sous-réseau sélectionnée, sinon la création de l'écouteur échoue.  
  
 **Adresse IPv4**  
 Si vous avez sélectionné l'adresse de sous-réseau IPv4 d'un sous-réseau, entrez une adresse IPv4 statique valide ici.  
  
 **Masque de sous-réseau**  
 Pour une adresse IPv4, ce champ en lecture seule affiche le masque de sous-réseau du sous-réseau sélectionné.  
  
 **Adresse IPv6**  
 Si vous avez sélectionné l'adresse de sous-réseau IPv6 d'un sous-réseau, entrez une adresse IPv6 statique valide ici.  
  
 **OK**  
 Cliquez pour créer et ajouter le sous-réseau dont vous avez sélectionné l'adresse, avec l'adresse IP statique que vous avez spécifiée. Une ligne contenant ces valeurs sera ajoutée à la grille de sous-réseau de la boîte de dialogue **Nouvel écouteur du groupe de disponibilité** ou **Spécifier les réplicas** .  
  
> [!IMPORTANT]  
>  La boîte de dialogue **Ajouter une adresse IP** ne vérifie pas l'adresse IP. De plus, la boîte de dialogue ne vous empêche pas d'ajouter la deuxième adresse de sous-réseau pour un sous-réseau que vous avez déjà ajouté à l'écouteur du groupe de disponibilité.  
  
 **Annuler**  
 Cliquez pour annuler vos sélections et revenir à la boîte de dialogue **Nouvel écouteur du groupe de disponibilité** ou à l’onglet **Écouteur** sans ajouter une adresse IP statique pour un sous-réseau.  
  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Connectivité Client AlwaysOn (SQL Server)](always-on-client-connectivity-sql-server.md)  
  
  
