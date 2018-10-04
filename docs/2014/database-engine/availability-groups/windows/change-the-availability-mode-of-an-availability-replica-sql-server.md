---
title: Changer le mode de disponibilité d’un réplica de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1fc60e637f9bf3d2e3b72f8b451c669d81a26207
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142289"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a>Modifier le mode de disponibilité d'un réplica de disponibilité (SQL Server)
  Cette rubrique explique comment modifier le mode de disponibilité d'un réplica de disponibilité dans un groupe de disponibilité AlwaysOn dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell. Le mode de disponibilité est une propriété de réplica qui contrôle si le réplica effectue la validation de façon synchrone ou asynchrone. Le*mode de validation asynchrone* optimise les performances au détriment d’une haute disponibilité et prend en charge uniquement le basculement forcé manuel (avec une possible perte de données), qu’on appelle généralement *basculement forcé*. Le*mode de validation synchrone* privilégie la haute disponibilité plutôt que les performances et, une fois que le réplica secondaire est synchronisé, prend en charge le basculement manuel et, éventuellement, le basculement automatique.  
  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour modifier le mode de disponibilité d'un groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez sur le groupe de disponibilité dont vous souhaitez modifier le réplica.  
  
4.  Cliquez avec le bouton droit sur le réplica, puis cliquez sur **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du réplica de disponibilité** , utilisez la liste déroulante **Mode de disponibilité** pour modifier le mode de disponibilité de ce réplica.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier le mode de disponibilité d'un groupe de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , comme suit :  
  
     ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     } )  
  
     où *group_name* est le nom du groupe de disponibilité et *server_name* est le nom de l’instance de serveur qui héberge le réplica à modifier.  
  
    > [!NOTE]  
    >  FAILOVER_MODE = AUTOMATIC n’est pris en charge que si vous spécifiez aussi AVAILABILITY_MODE = SYNCHRONOUS_COMMIT.  
  
     L'exemple suivant, écrit sur le réplica principal du groupe de disponibilité `AccountsAG` , modifie les modes de disponibilité et de basculement par une validation synchrone et un basculement automatique, pour le réplica hébergé par l'instance de serveur `INSTANCE09` .  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour modifier le mode de disponibilité d'un groupe de disponibilité**  
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez le `Set-SqlAvailabilityReplica` applet de commande avec le `AvailabilityMode` paramètre et, éventuellement, le `FailoverMode` paramètre.  
  
     Par exemple, la commande suivante modifie le réplica `MyReplica` dans le groupe de disponibilité `MyAg` afin qu'il utilise le mode de disponibilité avec validation synchrone et prenne en charge le basculement automatique.  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d’une applet de commande, utilisez le `Get-Help` applet de commande dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] environnement PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Modes de disponibilité (groupes de disponibilité AlwaysOn)](availability-modes-always-on-availability-groups.md)   
 [Basculement et Modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)  
  
  
