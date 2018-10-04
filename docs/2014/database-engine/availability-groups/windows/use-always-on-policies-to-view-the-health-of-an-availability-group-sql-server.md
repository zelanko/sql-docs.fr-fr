---
title: Utiliser les stratégies AlwaysOn pour afficher l’intégrité d’un groupe de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7937c507eda266669ba2040d202dac66559a242d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191359"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a>Utiliser les stratégies AlwaysOn pour afficher l'intégrité d'un groupe de disponibilité (SQL Server)
  Cette rubrique explique comment déterminer l'état opérationnel d'un groupe de disponibilité AlwaysOn à l'aide d'une stratégie AlwaysOn dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Pour plus d’informations sur la gestion basée sur AlwaysOn, consultez [stratégies AlwaysOn pour les problèmes opérationnels avec des groupes de disponibilité AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
> [!IMPORTANT]  
>  Pour les stratégies AlwaysOn, les noms de catégorie sont utilisés comme identificateurs. Modifier le nom d'une catégorie AlwaysOn compromettrait sa fonctionnalité d'évaluation de l'intégrité. Par conséquent, les noms de catégorie AlwaysOn ne doivent jamais être modifiés.  
  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert les autorisations CONNECT, VIEW SERVER STATE et VIEW ANY DEFINITION.  
  
##  <a name="SSMSProcedure"></a> À l’aide du tableau de bord AlwaysOn  
 **Pour ouvrir le tableau de bord AlwaysOn**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge l'un des réplicas de disponibilité. Pour afficher des informations sur tous les réplicas de disponibilité d'un groupe de disponibilité, utilisez l'instance de serveur qui héberge le réplica principal.  
  
2.  Cliquez sur le nom du serveur pour développer son arborescence.  
  
3.  Développez le nœud **Haute disponibilité AlwaysOn** .  
  
     Cliquez avec le bouton droit sur le nœud **Groupes de disponibilité** ou développez ce nœud et cliquez avec le bouton droit sur un groupe de disponibilité spécifique.  
  
4.  Sélectionnez la commande **Afficher le tableau de bord** .  
  
 Pour plus d’informations sur l’utilisation du tableau de bord AlwaysOn, consultez [Utiliser le tableau de bord AlwaysOn &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Utiliser les stratégies AlwaysOn pour afficher l’intégrité d’un groupe de disponibilité**  
  
1.  Définir par défaut (`cd`) à une instance de serveur qui héberge un des réplicas de disponibilité. Pour afficher des informations sur tous les réplicas de disponibilité d'un groupe de disponibilité, utilisez l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez les applets de commande suivantes :  
  
     `Test-SqlAvailabilityGroup`  
     Évalue l'intégrité d'un groupe de disponibilité lors de l'évaluation des stratégies de gestion basées sur des stratégies SQL Server. Vous devez disposer des autorisations CONNECT, VIEW SERVER STATE et VIEW ANY DEFINITION pour exécuter cette applet de commande.  
  
     Par exemple, la commande suivante affiche tous les groupes de disponibilité avec l’état d’intégrité « Erreur » sur l’instance de serveur `Computer\Instance`.  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups `   
    | Test-SqlAvailabilityGroup | Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     Évalue l'intégrité des réplicas de disponibilité lors de l'évaluation des stratégies de gestion basées sur des stratégies SQL Server. Vous devez disposer des autorisations CONNECT, VIEW SERVER STATE et VIEW ANY DEFINITION pour exécuter cette applet de commande.  
  
     Par exemple, la commande suivante évalue l'intégrité du réplica de disponibilité nommé `MyReplica` dans le groupe de disponibilité `MyAg` et génère un bref résumé.  
  
    ```  
    Test-SqlAvailabilityReplica `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     Évalue l'intégrité d'une base de données de disponibilité sur tous les réplicas de disponibilité joints par l'évaluation des stratégies de gestion basées sur des stratégies SQL Server.  
  
     Par exemple, la commande suivante évalue l'intégrité de toutes les bases de données de disponibilité du groupe de disponibilité `MyAg` et génère un bref résumé pour chaque base de données.  
  
    ```  
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates `   
     | Test-SqlDatabaseReplicaState  
    ```  
  
     Ces applets de commande acceptent les options suivantes :  
  
    |Option|Description|  
    |------------|-----------------|  
    |`AllowUserPolicies`|Exécute des stratégies d'utilisateur présentes dans les catégories de stratégie AlwaysOn.|  
    |`InputObject`|Collection d'objets qui représentent des groupes de disponibilité, des réplicas de disponibilité ou des états de base de données de disponibilité (selon les applets de commande que vous utilisez). L'applet de commande calcule l'intégrité des objets spécifiés.|  
    |`NoRefresh`|Lorsque ce paramètre est défini, l’applet de commande n’actualise pas manuellement les objets spécifiés par le `-Path` ou `-InputObject` paramètre.|  
    |`Path`|Chemin d'accès au groupe de disponibilité, à un ou plusieurs réplicas de disponibilité ou à l'état de cluster de réplica de la base de données de disponibilité (selon les applets de commande que vous utilisez). Il s'agit d'un paramètre facultatif. Si elle n'est pas spécifiée, la valeur de ce paramètre est définie par défaut à l'emplacement de travail actuel.|  
    |`ShowPolicyDetails`|Indique le résultat de chaque évaluation de la stratégie exécutée par cette applet de commande. L'applet de commande génère un objet par évaluation de stratégie, et cet objet comporte des champs décrivant les résultats de l'évaluation (que la stratégie ait réussi ou non, le nom de la stratégie et la catégorie, etc.).|  
  
     Par exemple, la commande `Test-SqlAvailabilityGroup` suivante spécifie le paramètre `-ShowPolicyDetails` pour afficher le résultat de chaque évaluation de stratégie exécutée par cette applet de commande pour chaque stratégie de gestion basée sur des stratégies (PBM) exécutée sur le groupe de disponibilité nommé `MyAg`.  
  
    ```  
    Test-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName `  
    -ShowPolicyDetails  
  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d’une applet de commande, utilisez le `Get-Help` applet de commande dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] environnement PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
 **Blogs de l’équipe AlwaysOn SQL Server, analyse l’intégrité AlwaysOn avec PowerShell :**  
  
-   [Partie 1 : Vue d'ensemble de l'applet de commande](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
-   [Partie 2 : Utilisation avancée de l'applet de commande](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
-   [Partie 3 : Application de surveillance simple](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
-   [Partie 4 : Intégration à l'Agent SQL Server](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Administration d’un groupe de disponibilité &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [Surveillance des groupes de disponibilité &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Stratégies AlwaysOn pour les problèmes opérationnels avec des groupes de disponibilité AlwaysOn (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  
