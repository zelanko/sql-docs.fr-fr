---
title: Administration automatisée à l’échelle d’une entreprise | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 95ed4df18cfb4bcf433d08bbe9decacf35977c0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143825"
---
# <a name="automated-administration-across-an-enterprise"></a>Administration automatisée à l'échelle d'une entreprise
  Le fait d’automatiser l’administration sur plusieurs instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est appelé *administration multiserveur*. Utilisez l'administration multiserveur dans les cas suivants :  
  
-   Gérez deux serveurs ou plus ;  
  
-   Planifiez les flux d'informations entre les serveurs de l'entreprise pour constituer un Data Warehouse.  
  
> [!NOTE]  
>  Dans le cadre des efforts constants de [!INCLUDE[msCoName](../../includes/msconame-md.md)] visant à réduire le coût total de possession, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a proposé deux nouvelles fonctionnalités : une méthode de gestion de serveurs appelée Gestion basée sur des stratégies et des requêtes multiserveurs qui utilisent des serveurs de configuration et des groupes de serveurs. Ces fonctionnalités peuvent être utilisées avec, ou au lieu de, certaines des fonctionnalités décrites dans cette rubrique. Pour plus d’informations, consultez [administrer des serveurs par la gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) et [administrer plusieurs serveurs à l’aide de serveurs de gestion centralisée](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).  
  
 Pour tirer parti d'une administration multiserveur, vous devez disposer d'au moins un serveur maître et d’au moins un serveur cible. Un serveur maître distribue les travaux aux serveurs cibles et reçoit les événements de ces derniers. Un serveur maître stocke également la copie centrale des définitions de travaux pour les travaux exécutés sur des serveurs cibles. Les serveurs cibles se connectent régulièrement au serveur maître pour mettre à jour leur liste des travaux planifiés. Si un nouveau travail se trouve sur le serveur maître, le serveur cible le télécharge. Une fois que le serveur cible a terminé le travail, il se reconnecte au serveur maître et rend compte de l'état du travail.  
  
 L'illustration suivante décrit la relation entre serveurs maîtres et cibles :  
  
 ![Configuration de l’administration multiserveur](../../database-engine/media/multisvr.gif "Configuration de l’administration multiserveur")  
  
 Si vous administrez les serveurs départementaux d'une grande société, vous pouvez définir les éléments suivants :  
  
-   un travail de sauvegarde en plusieurs étapes ;  
  
-   les opérateurs à avertir en cas d'échec de sauvegarde ;  
  
-   un programme d'exécution pour le travail de sauvegarde.  
  
 Écrivez ce travail de sauvegarde une seule fois sur le serveur maître, puis inscrivez chaque serveur du service comme serveur cible dans le serveur maître. Dès lors qu'ils sont inscrits, tous les serveurs départementaux exécutent le même travail de sauvegarde, alors que vous n'avez défini le travail qu'une seule fois.  
  
> [!NOTE]  
>  Les fonctionnalités d'administration multiserveur s'adressent aux membres du rôle sysadmin. Cependant, un membre du rôle sysadmin sur le serveur cible ne peut pas modifier les opérations exécutées sur le serveur cible par le serveur maître. Cette mesure de sécurité empêche la suppression accidentelle des étapes du travail et l’interruption des opérations sur le serveur cible.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Créer un environnement multi-serveur](create-a-multiserver-environment.md)  
 Contient des informations sur la création et la gestion des serveurs maîtres et cibles.  
  
 [Choisir le compte de service SQL Server Agent correct pour les environnements multiserveurs](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 Contient des informations sur la manière dont l'utilisation de comptes Windows non administratifs ou du compte système local pour le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent peut affecter les environnements multiserveurs.  
  
 [Définir des options de chiffrement sur des serveurs cibles](set-encryption-options-on-target-servers.md)  
 Contient des informations sur la définition de la sous-clé de Registre[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent MsxEncryptChannelOptions sur les serveurs cibles.  
  
 [Gérer des travaux à l'échelle d'une entreprise](manage-jobs-across-an-enterprise.md)  
 Contient des informations concernant la vérification de l'état des travaux, la modification des serveurs cibles pour les travaux, la synchronisation des horloges des serveurs cibles et l'interrogation des serveurs maîtres quant à l'état des travaux en cours.  
  
 [Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 Contient des informations relatives au dépannage des travaux multiserveurs qui utilisent des proxys qui échouent.  
  
 [Interroger des serveurs](poll-servers.md)  
 Contient des informations sur la façon de configurer de manière implicite et explicite les serveurs cibles, de sorte qu'ils interrogent les serveurs maîtres pour la synchronisation des informations sur les travaux.  
  
 [Gérer les événements](manage-events.md)  
 Contient des informations concernant le transfert d'événements des serveurs cibles vers les serveurs maîtres.  
  
 [Paramétrer l'administration automatisée dans une entreprise](tune-automated-administration-across-an-enterprise.md)  
 Contient des informations décrivant la façon dont l'administration automatisée au sein d'un environnement multiserveur exploite les fonctionnalités d'autoconfiguration de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante du moteur de base de données SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Inscrire des serveurs](../register-servers/register-servers.md)   
 [sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql)   
 [sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql)   
 [sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql)   
 [sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql)   
 [dbo.sysjobservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql)   
 [Sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)   
 [dbo.systargetservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
