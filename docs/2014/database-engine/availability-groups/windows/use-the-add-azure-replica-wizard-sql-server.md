---
title: Utiliser l’Assistant Ajout d’un réplica Azure (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 90418193ac869641a20f8b0f684fc43dd46712f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70175997"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Utiliser l'Assistant Ajout d’un réplica Azure (SQL Server)
  Utilisez l’Assistant Ajout d’un réplica Azure pour vous aider à créer une machine virtuelle Azure dans un environnement informatique hybride et à le configurer comme réplica secondaire pour un groupe de disponibilité AlwaysOn nouveau ou existant.  
  
-   **Avant de commencer :**  
  
     [Prérequis](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour ajouter un réplica à l’aide de :**  [Assistant Ajouter un réplica Azure (SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Si vous n’avez jamais ajouté de réplica de disponibilité à un groupe de disponibilité, consultez les sections « instances de serveur » et « groupes de disponibilité et réplicas » dans [conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Prerequisites"></a>Conditions préalables  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal actuel.  
  
-   Vous devez travailler dans un environnement informatique hybride où votre sous-réseau local dispose d’un réseau privé virtuel (VPN) de site à site avec Azure. Pour plus d’informations, consultez [Configurer un réseau privé virtuel (VPN) de site à site dans le portail de gestion](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Votre groupe de disponibilité doit contenir des réplicas de disponibilité locaux.  
  
-   Les clients de l’écouteur de groupe de disponibilité doivent disposer d’une connectivité à Internet s’ils souhaitent maintenir la connectivité avec l’écouteur lorsque le groupe de disponibilité est basculé vers un réplica Azure.  
  
-   **Conditions préalables à l’utilisation de la synchronisation de données initiale complète** Vous devez spécifier un partage réseau pour que l’Assistant crée des sauvegardes et accède à celles-ci. Pour le réplica principal, le compte utilisé pour démarrer le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] doit disposer d'autorisations de système de fichiers en lecture et en écriture sur un partage réseau. Pour les réplicas secondaires, le compte doit disposer d'une autorisation en lecture sur le partage réseau.  
  
     Si vous ne pouvez pas utiliser l'Assistant pour effectuer la synchronisation des données initiale complète, vous devez préparer vos bases de données secondaires manuellement. Vous pouvez le faire avant ou après l'exécution de l'Assistant. Pour plus d’informations, consultez [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Consultez [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)  
  
##  <a name="SSMSProcedure"></a>Utilisation de l’Assistant Ajout d’un réplica Azure (SQL Server Management Studio)  
 L'Assistant Ajouter un réplica Windows Azure peut être lancé depuis la page [Spécifier les réplicas](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md). Il existe deux moyens d'atteindre cette page :  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 Une fois que vous avez lancé l'Assistant Ajouter un réplica Windows Azure, suivez les étapes ci-dessous :  
  
1.  Commencez par télécharger un certificat de gestion pour votre abonnement Azure. Cliquez sur **Télécharger** pour ouvrir la page de connexion.  
  
2.  Dans la page de connexion, connectez-vous à votre abonnement Azure. Une fois que vous êtes connecté, l'Assistant installe un certificat de gestion sur votre ordinateur local. Ce certificat de gestion sera chargé automatiquement lorsque vous utiliserez à nouveau cet Assistant. Si vous avez téléchargé plusieurs certificats de gestion, vous pouvez cliquer sur le bouton **...** pour sélectionner celui à utiliser.  
  
3.  Connectez-vous ensuite à votre abonnement en cliquant sur **Connexion**. Une fois que vous êtes connecté, les listes déroulantes sont remplies avec vos paramètres Azure, tels que **Réseau virtuel** et **Sous-réseau de réseau virtuel**.  
  
4.  Spécifiez les paramètres de la machine virtuelle Azure qui hébergera le nouveau réplica secondaire :  
  
     Image  
     Nom de l’image SQL Server à utiliser pour la machine virtuelle Azure  
  
     Taille de la machine virtuelle  
     Taille de la machine virtuelle Azure  
  
     Nom de la machine virtuelle  
     Nom DNS de la machine virtuelle Azure  
  
     Nom d'utilisateur de l'ordinateur virtuel  
     Nom d’utilisateur de l’administrateur par défaut de la machine virtuelle Azure  
  
     Mot de passe d'administrateur de l'ordinateur virtuel (et Confirmer le mot de passe)  
     Mot de passe de l’administrateur par défaut de la machine virtuelle Azure  
  
     Réseau virtuel  
     Réseau virtuel dans lequel placer la machine virtuelle Azure  
  
     Sous-réseau de réseau virtuel  
     Sous-réseau de réseau virtuel dans lequel placer la machine virtuelle Azure  
  
     Domain  
     Domaine Active Directory (AD) auquel joindre la machine virtuelle Azure  
  
     Domain Username  
     Nom d’utilisateur AD utilisé pour joindre la machine virtuelle Azure au domaine  
  
     Mot de passe  
     Mot de passe utilisé pour joindre la machine virtuelle Azure au domaine  
  
5.  Cliquez sur **OK** pour valider vos paramètres et quitter l'Assistant Ajouter un réplica Windows Azure.  
  
6.  Effectuez les autres étapes de configuration décrites à la page [Spécifier les réplicas](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) , comme vous le feriez pour tout nouveau réplica.  
  
     Une fois que vous avez terminé avec l’Assistant groupe de disponibilité ou l’Assistant Ajouter un réplica au groupe de disponibilité, le processus de configuration effectue toutes les opérations dans Azure pour créer le nouvel ordinateur virtuel, le joindre au domaine AD, l’ajouter au cluster Windows, activer la haute AlwaysOn Disponibilité, puis ajoutez le nouveau réplica au groupe de disponibilité.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
