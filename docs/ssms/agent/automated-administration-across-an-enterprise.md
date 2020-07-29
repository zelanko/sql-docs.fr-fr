---
title: Administration automatisée à l'échelle d'une entreprise
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 17356ab4630dfb981fd359caa48a22dac51f6c94
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749199"
---
# <a name="automated-administration-across-an-enterprise"></a>Administration automatisée à l'échelle d'une entreprise
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Le fait d’automatiser l’administration sur plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est appelé *administration multiserveur*. Utilisez l'administration multiserveur dans les cas suivants :  
  
-   Gérez deux serveurs ou plus ;  
  
-   Planifiez les flux d'informations entre les serveurs de l'entreprise pour constituer un Data Warehouse.  
  
Pour tirer parti d'une administration multiserveur, vous devez disposer d'au moins un serveur maître et d’au moins un serveur cible. Un serveur maître distribue les travaux aux serveurs cibles et reçoit les événements de ces derniers. Un serveur maître stocke également la copie centrale des définitions de travaux pour les travaux exécutés sur des serveurs cibles. Les serveurs cibles se connectent régulièrement au serveur maître pour mettre à jour leur liste des travaux planifiés. Si un nouveau travail se trouve sur le serveur maître, le serveur cible le télécharge. Une fois que le serveur cible a terminé le travail, il se reconnecte au serveur maître et rend compte de l'état du travail. Notez que votre définition de travail doit être identique lors de l’exécution de toute activité liée aux bases de données.  
  
L'illustration suivante décrit la relation entre serveurs maîtres et cibles :  
  
![Configuration d'administration multiserveur](../../ssms/agent/media/multisvr.gif "Configuration d'administration multiserveur")  
  
Si vous administrez les serveurs départementaux d'une grande société, vous pouvez définir les éléments suivants :  
  
-   un travail de sauvegarde en plusieurs étapes ;  
  
-   les opérateurs à avertir en cas d'échec de sauvegarde ;  
  
-   un programme d'exécution pour le travail de sauvegarde.  
  
Écrivez ce travail de sauvegarde une seule fois sur le serveur maître, puis inscrivez chaque serveur du service comme serveur cible dans le serveur maître. Dès lors qu'ils sont inscrits, tous les serveurs départementaux exécutent le même travail de sauvegarde, alors que vous n'avez défini le travail qu'une seule fois.  
  
> [!NOTE]  
> Les fonctionnalités d'administration multiserveur s'adressent aux membres du rôle sysadmin. Cependant, un membre du rôle sysadmin sur le serveur cible ne peut pas modifier les opérations exécutées sur le serveur cible par le serveur maître. Cette mesure de sécurité empêche la suppression accidentelle des étapes du travail et l’interruption des opérations sur le serveur cible.  
  
## <a name="in-this-section"></a>Dans cette section  
[Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)  
Contient des informations sur la création et la gestion des serveurs maîtres et cibles.  
  
[Choisir le compte de service SQL Server Agent correct pour les environnements multiserveurs](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
Contient des informations sur la manière dont l'utilisation de comptes Windows non administratifs ou du compte système local pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut affecter les environnements multiserveurs.  
  
[Définir des options de chiffrement sur des serveurs cibles](../../ssms/agent/set-encryption-options-on-target-servers.md)  
Contient des informations sur la définition de la sous-clé de Registre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent MsxEncryptChannelOptions sur les serveurs cibles.  
  
[Gérer des travaux à l'échelle d'une entreprise](../../ssms/agent/manage-jobs-across-an-enterprise.md)  
Contient des informations concernant la vérification de l'état des travaux, la modification des serveurs cibles pour les travaux, la synchronisation des horloges des serveurs cibles et l'interrogation des serveurs maîtres quant à l'état des travaux en cours.  
  
[Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
Contient des informations relatives au dépannage des travaux multiserveurs qui utilisent des proxys qui échouent.  
  
[Interroger des serveurs](../../ssms/agent/poll-servers.md)  
Contient des informations sur la façon de configurer de manière implicite et explicite les serveurs cibles, de sorte qu'ils interrogent les serveurs maîtres pour la synchronisation des informations sur les travaux.  
  
[Gérer les événements](../../ssms/agent/manage-events.md)  
Contient des informations concernant le transfert d'événements des serveurs cibles vers les serveurs maîtres.  
  
[Paramétrer l'administration automatisée dans une entreprise](../../ssms/agent/tune-automated-administration-across-an-enterprise.md)  
Contient des informations décrivant la façon dont l'administration automatisée au sein d'un environnement multiserveur exploite les fonctionnalités d'autoconfiguration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[Rubriques relatives à la compatibilité descendante pour l’installation du moteur de base de données SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)  
[Inscription des serveurs](../register-servers/register-servers.md)  
[sp_add_targetservergroup](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)  
[sp_delete_targetserver](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)  
[sp_delete_targetservergroup](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)  
[_sp_help_downloadlist](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)  
[sp_help_jobserver](../../relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql.md)  
[sp_help_targetservergroup](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)  
[sp_resync_targetserver](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)  
[sp_update_targetservergroup](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)  
[sysjobservers](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)  
[syslogins](../../relational-databases/system-compatibility-views/sys-syslogins-transact-sql.md)  
[systargetservers](../../relational-databases/system-tables/dbo-systargetservers-transact-sql.md)  
  
