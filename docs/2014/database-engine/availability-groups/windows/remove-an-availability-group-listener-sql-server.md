---
title: Supprimer un écouteur de groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 049296ff601296edbd990fe9ea70aef3efa8c44b
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72782856"
---
# <a name="remove-an-availability-group-listener-sql-server"></a>Supprimer un écouteur de groupe de disponibilité (SQL Server)
  Cette rubrique explique comment supprimer un écouteur de groupe de disponibilité d'un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Avant de commencer :**  
  
     [Prérequis](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un écouteur à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Prérequis  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
###  <a name="Recommendations"></a> Recommandations  
 Avant de supprimer un écouteur de groupe de disponibilité, nous vous recommandons de vérifier qu'aucune application ne l'utilise.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour supprimer un écouteur de groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal, cliquez sur le nom du serveur pour développer l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Développez le nœud du groupe de disponibilité, puis développez le nœud **Écouteurs de groupe de disponibilité** .  
  
4.  Cliquez avec le bouton droit sur l’écouteur à supprimer et sélectionnez la commande **Supprimer** .  
  
5.  Cela ouvre la boîte de dialogue **Supprimer l'écouteur du groupe de disponibilité** . Pour plus d'informations, consultez [Supprimer l'écouteur du groupe de disponibilité](#AgListenerPropertiesDialog), plus loin dans cette rubrique.  
  
###  <a name="AgListenerPropertiesDialog"></a> Supprimer l'écouteur du groupe de disponibilité (boîte de dialogue)  
 **Nom**  
 Nom de l'écouteur à supprimer.  
  
 **Result**  
 Affiche un lien, **Opération réussie** ou **Erreur**, sur lequel vous pouvez cliquer pour plus d’informations.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour supprimer un écouteur de groupe de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , comme suit :  
  
     ALTER AVAILABILITY GROUP *nom_groupe* Remove listener **' *`dns_name`* '**  
  
     où *nom_groupe* est le nom du groupe de disponibilité et *nom_dns* est le nom DNS de l’écouteur du groupe de disponibilité.  
  
     L'exemple suivant supprime l'écouteur du groupe de disponibilité `AccountsAG` . Le nom DNS est AccountsAG_Listener.  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour supprimer un écouteur de groupe de disponibilité**  
  
1.  Définissez la valeur par défaut (`cd`) sur l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'applet de commande `Remove-Item` intégrée pour supprimer un écouteur. Par exemple, la commande suivante supprime un écouteur nommé `MyListener` d'un groupe de disponibilité nommé `MyAg`.  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
##  <a name="RelatedTasks"></a> Tâches connexes  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Afficher les propriétés d’écouteur de groupe de disponibilité &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble &#40;de&#41; groupes de disponibilité AlwaysOn SQL Server](overview-of-always-on-availability-groups-sql-server.md)    
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)  
