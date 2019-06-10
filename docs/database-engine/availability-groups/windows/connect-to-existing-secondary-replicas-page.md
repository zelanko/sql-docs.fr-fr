---
title: Page « Se connecter à des réplicas secondaires existants » pour les groupes de disponibilité
description: Description des différentes options disponibles dans la page « Se connecter à des réplicas secondaires existants » de « l’Assistant Groupe de disponibilité » dans SQL Server Management Studio.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.adddatabasewizard.connecttoreplicas.f1
- sql13.swb.addreplicawizard.connecttoreplicas.f1
ms.assetid: 850f1bc8-d7d0-425c-bd7b-03f0e9d3348e
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 40350310858415cd7e5451bbd2f99e9d00ddbf4a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66793567"
---
# <a name="connect-to-existing-secondary-replicas-page---always-on-availability-groups"></a>Page « Se connecter à des réplicas secondaires existants » pour les groupes de disponibilité Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique d’aide décrit les options de la page **Se connecter à des réplicas secondaires existants** . Cette rubrique est utilisée par l' [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] et par l' [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Colonnes de la grille :**  
 **Instance de serveur**  
 Affiche le nom de l'instance du serveur qui hébergera le réplica de disponibilité.  
  
 **Connecté en tant que**  
 Affiche le compte qui est connecté à l'instance de serveur, une fois que la connexion a été établie. Si cette colonne affiche «**Non connecté**» pour une instance de serveur donnée, vous devez cliquer sur le bouton **Se connecter** ou **Se connecter à tous** .  
  
 **Se connecter**  
 Cliquez sur ce bouton si cette instance de serveur s'exécute sous un compte différent de celui des autres instances de serveur auxquelles vous devez vous connecter.  
  
 **Se connecter à tous**  
 Cliquez sur ce bouton uniquement si chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à laquelle vous devez vous connecter s'exécute en tant que service dans le même compte d'utilisateur.  
  
 **Annuler**  
 Cliquez pour annuler l'Assistant. Dans la page **Se connecter à des réplicas secondaires existants** , l’annulation de l’Assistant provoque sa fermeture sans effectuer aucune action.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
