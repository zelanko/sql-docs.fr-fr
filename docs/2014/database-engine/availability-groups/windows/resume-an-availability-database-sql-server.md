---
title: Reprendre une base de données de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a2279940c2502a310e9dac4448bd6029b6e13dc
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936520"
---
# <a name="resume-an-availability-database-sql-server"></a>Reprendre une base de données de disponibilité (SQL Server)
  Vous pouvez reprendre une base de données de disponibilité interrompue dans [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. La reprise d'une base de données interrompue met la base de données dans l'état SYNCHRONIZING. La reprise de la base de données primaire rétablit également toutes ses bases de données secondaires qui ont été interrompues suite à l'interruption de la base de données primaire. Si une base de données secondaire a été interrompue localement, depuis l'instance de serveur qui héberge le réplica secondaire, cette base de données secondaire doit être reprise localement. Une fois qu'une base de données secondaire particulière et que la base de données principale correspondante sont dans l'état SYNCHRONIZING, la synchronisation des données reprend sur la base de données secondaire.  
  
> [!NOTE]  
>  La suspension et la reprise d'une base de données secondaire AlwaysOn n'affectent pas directement la disponibilité de la base de données primaire. Toutefois, l'interruption d'une base de données secondaire peut avoir un impact sur la redondance et les fonctions de basculement de la base de données primaire, jusqu'à ce que la base de données secondaire interrompue reprenne. Ce comportement diffère de la mise en miroir de bases de données dans laquelle l'état de mise en miroir est interrompu à la fois sur la base de données miroir et la base de données principale tant que la mise en miroir n'a pas repris. L'interruption d'une base de données principale AlwaysOn interrompt le déplacement des données sur toutes les bases de données secondaires correspondantes, et les capacités de redondance et de basculement cessent pour cette base de données tant que la base de données principale n'a pas repris.  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Composants requis](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour reprendre une base de données secondaire, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
 Une commande RESUME retourne dès qu'elle est acceptée par le réplica qui héberge la base de données cible, mais en réalité, la reprise de la base de données se produit de façon asynchrone.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez être connecté à l'instance de serveur qui héberge la base de données à reprendre.  
  
-   Le groupe de disponibilité doit être en ligne.  
  
-   La base de données primaire doit être en ligne et disponible.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour reprendre une base de données secondaire**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica de disponibilité sur lequel vous souhaitez reprendre une base de données et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Développez le groupe de disponibilité.  
  
4.  Développez le nœud **Bases de données de disponibilité** , cliquez avec le bouton droit sur la base de données, puis sélectionnez **Reprendre le déplacement des données**.  
  
5.  Dans la boîte de dialogue **Reprendre le déplacement des données** , cliquez sur **OK**.  
  
> [!NOTE]  
>  Pour reprendre des bases de données supplémentaires sur cet emplacement de réplica, répétez les étapes 4 et 5 pour chaque base de données.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour reprendre une base de données secondaire qui a été suspendue localement**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica secondaire dont vous souhaitez reprendre la base de données.  
  
2.  Reprenez la base de données secondaire à l’aide de l’instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)suivante :  
  
     Instruction ALTER DATABASE *database_name* Set Hadr Resume  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  

### <a name="to-resume-a-secondary-database"></a>Pour reprendre une base de données secondaire
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur qui héberge le réplica dont vous souhaitez reprendre la base de données. Pour plus d'informations, consultez [Conditions préalables requises](#Prerequisites), plus haut dans cette rubrique.  
  
2.  Utilisez l’applet de commande **Resume-SqlAvailabilityDatabase** pour reprendre le groupe de disponibilité.  
  
     Par exemple, la commande suivante reprend la synchronisation des données pour la base de données de disponibilité `MyDb3` dans le groupe de disponibilité `MyAg`.  
  
    ```powershell
    Resume-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Interrompre une base de données de disponibilité &#40;SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
