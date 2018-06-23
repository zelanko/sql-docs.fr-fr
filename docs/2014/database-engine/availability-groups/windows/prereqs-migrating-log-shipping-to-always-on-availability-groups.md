---
title: Conditions préalables pour la migration à partir de journaux de transaction vers les groupes de disponibilité AlwaysOn (SQL Server) | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: e01e7b373318e64370cc48ff79002c130bd0838a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140091"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a>Conditions préalables requises pour la migration de la copie des journaux de transaction vers les groupes de disponibilité AlwaysOn (SQL Server)
  Cette rubrique décrit les conditions requises pour convertir une base de données principale pour la copie des journaux de transaction avec une ou plusieurs de ses bases de données secondaires en base de données principale AlwaysOn et ses bases de données secondaires.  
  
> [!NOTE]  
>  Vous pouvez configurer une base de données principale ou secondaire (éventuellement accessible en lecture) dans un groupe de disponibilité en tant que base de données principale de copie des journaux de transaction.  
  
 **Dans cette rubrique :**  
  
-   [Conditions préalables requises pour les groupes de disponibilité](#AGPrereqsRealAddress)  
  
-   [Conditions préalables requises pour la copie des journaux de transaction](#LogShipPrereqs)  
  
-   [Tâches associées](#RelatedTasks)  
  
-   [Contenu connexe](#RelatedContent)  
  
##  <a name="AGPrereqsRealAddress"></a> Conditions préalables requises pour les groupes de disponibilité  
 Pour permettre aux travaux de sauvegarde de s'exécuter sur le réplica principal du groupe de disponibilité, utilisez les paramètres de sauvegarde de groupes de disponibilité AlwaysOn suivants :  
  
|Propriété|Paramètre|  
|--------------|-------------|  
|Préférence de sauvegarde automatisée du groupe de disponibilité|Uniquement sur le réplica principal|  
|Priorité de sauvegarde du réplica principal.|>0|  
  
 **Pour plus d'informations, consultez :**  
  
 [Afficher les propriétés d’un groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)  
  
 [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="LogShipPrereqs"></a> Conditions préalables requises pour la copie des journaux de transaction  
  
-   La base de données principale pour la copie des journaux de transaction doit résider sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica principal initial/actuel du groupe de disponibilité.  
  
-   Pour qu'une base de données secondaire pour la copie des journaux de transaction soit convertie en base de données secondaire AlwaysOn, procédez comme suit :  
  
    -   Utilisez le même nom que celui de la base de données principale.  
  
    -   Choisissez un emplacement sur une instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité.  
  
 Une fois que le travail de sauvegarde a été exécuté sur la base de données principale, désactivez-le. Dès que le travail de restauration a été exécuté sur une base de données secondaire donnée, désactivez-le.  
  
 Après avoir créé toutes les bases de données secondaires pour le groupe de disponibilité, si vous souhaitez effectuer des sauvegardes sur des réplicas secondaires, vous devez reconfigurer la préférence de sauvegarde automatisée du groupe de disponibilité.  
  
 **Pour plus d'informations, consultez :**  
  
 [Converting a logshipping configuration to Availability Group](http://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (Conversion d’une configuration de copie de journaux de transaction en groupe de disponibilité - blog SQL Server)  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Envoi des journaux de transaction**  
  
-   [Mise à niveau des journaux de transaction vers SQL Server 2014 &#40;Transact-SQL&#41;](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Supprimer la copie des journaux de transaction &#40;SQL Server&#41;](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 **Groupes de disponibilité AlwaysOn**  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Créer un groupe de disponibilité &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [Converting a logshipping configuration to Availability Group](http://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx)  
  
     [Ajouter une base de données primaire de copie des journaux de transaction et une base de données secondaire à un groupe de disponibilité existant](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/01/use-log-shipping-to-prepare-secondary-databases-for-an-existing-availability-group.aspx)  
  
     [Blogs de l’équipe AlwaysOn SQL Server : Le Blog officiel de SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **Livres blancs :**  
  
     [Guide de migration : Migration vers les groupes de disponibilité AlwaysOn à partir des déploiements antérieurs combinant la mise en miroir de base de données et journaux de transaction](http://msdn.microsoft.com/library/jj635217)  
  
     [Livres blancs de Microsoft pour SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md)   
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  