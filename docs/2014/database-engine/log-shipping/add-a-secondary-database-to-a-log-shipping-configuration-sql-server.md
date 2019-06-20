---
title: Ajouter une base de données secondaire dans une configuration de copie des journaux de transaction (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 22f1fbc9470eb4002bb40f0e4e513f35134c442e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62774349"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a>Ajouter une base de données secondaire dans une configuration de copie des journaux de transaction (SQL Server)
  Cette rubrique explique comment ajouter une base de données secondaire à une configuration de copie des journaux de transaction dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour ajouter une base de données secondaire pour la copie des journaux de transaction, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les procédures stockées de copie des journaux de transaction nécessitent l’appartenance au rôle serveur fixe **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a>Pour ajouter une base de données secondaire pour la copie des journaux de transaction  
  
1.  Cliquez avec le bouton droit sur la base de données à utiliser en tant que base de données primaire dans la configuration de copie des journaux de transaction, puis sélectionnez **Propriétés**.  
  
2.  Sous **Sélectionner une page**, cliquez sur **Envoi de journaux de transaction**.  
  
3.  Sous **Instances de serveurs et bases de données secondaires**, cliquez sur **Ajouter**.  
  
4.  Cliquez sur **Se connecter** et connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser comme serveur secondaire.  
  
5.  Dans la zone **Base de données secondaire** , choisissez une base de données dans la liste ou tapez le nom de la base de données que vous voulez créer.  
  
6.  Dans l'onglet **Initialiser la base de données secondaire** , choisissez l'option à utiliser pour initialiser la base de données secondaire.  
  
7.  Dans l' **onglet Copier les fichiers**, dans la zone **Dossier de destination des fichiers copiés** , entrez le chemin du dossier vers lequel vous voulez copier les sauvegardes des journaux des transactions. Ce dossier se situe généralement sur le serveur secondaire.  
  
8.  Notez la planification de la copie figurant dans la zone **Planification** sous **Copier le travail**. Si vous souhaitez personnaliser la planification de votre installation, cliquez sur **Planification** et ajustez ensuite la planification de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en fonction de vos besoins. Cette planification doit être proche de la planification de la sauvegarde.  
  
9. Dans l’onglet **Restaurer** , sous **État de la base de données lors de la restauration des sauvegardes**, choisissez l’option **Aucun mode de récupération** ou **Mode veille** .  
  
10. Si vous choisissez l'option **Mode veille** , déterminez si vous voulez déconnecter des utilisateurs de la base de données secondaire pendant que l'opération de restauration est en cours.  
  
11. Si vous voulez retarder le processus de restauration sur le serveur secondaire, choisissez un délai sous **Retarder la restauration des sauvegardes d'au moins**.  
  
12. Choisissez un seuil d'alerte sous **Envoyer une alerte si aucune restauration ne se produit dans l'espace de**.  
  
13. Notez la planification de la restauration figurant dans la zone **Planification** sous **Restaurer le travail**. Si vous souhaitez personnaliser la planification de votre installation, cliquez sur **Planification** et ajustez ensuite la planification de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en fonction de vos besoins. Cette planification doit être proche de la planification de la sauvegarde.  
  
14. Cliquez sur **OK**.  
  
15. Cliquez sur **OK** dans la boîte de dialogue Propriétés de la base de données pour démarrer la procédure de configuration.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a>Pour ajouter une base de données secondaire pour la copie des journaux de transaction  
  
1.  Sur le serveur secondaire, exécutez [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) en fournissant les informations sur le serveur et la base de données principaux. Cette procédure stockée retourne l'ID secondaire et les ID des travaux de copie et de restauration.  
  
2.  Sur le serveur secondaire, exécutez [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) pour définir la planification des travaux de copie et de restauration.  
  
3.  Sur le serveur secondaire, exécutez [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) pour ajouter une base de données secondaire.  
  
4.  Sur le serveur principal, exécutez [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) pour ajouter les informations requises sur la nouvelle base de données secondaire au serveur principal.  
  
5.  Sur le serveur secondaire, activez les travaux de copie et de restauration. Pour plus d’informations, consultez [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Mettre à niveau des journaux de transaction vers SQL Server 2014 &#40;Transact-SQL&#41;](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Configurer la copie des journaux de transaction &#40;Transact-SQL&#41;](configure-log-shipping-sql-server.md)  
  
-   [Supprimer une base de données secondaire dans une configuration de copie des journaux de transaction &#40;SQL Server&#41;](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [Supprimer la copie des journaux de transaction &#40;SQL Server&#41;](remove-log-shipping-sql-server.md)  
  
-   [Afficher le rapport de la copie des journaux de transaction &#40;SQL Server Management Studio&#41;](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Surveiller la copie des journaux de transaction &#40;Transact-SQL&#41;](monitor-log-shipping-transact-sql.md)  
  
-   [Basculer vers une base de données secondaire de copie des journaux de transaction &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](about-log-shipping-sql-server.md)   
 [Tables et procédures stockées liées à la copie des journaux de transaction](log-shipping-tables-and-stored-procedures.md)  
  
  
