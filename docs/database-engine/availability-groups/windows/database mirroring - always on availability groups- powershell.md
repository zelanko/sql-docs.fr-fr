---
title: "Cr&#233;er un point de terminaison de mise en miroir de bases de donn&#233;es pour les groupes de disponibilit&#233; Always On (SQL Server PowerShell) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Groupes de disponibilité [SQL Server], instance de serveur"
  - "Groupes de disponibilité [SQL Server], déploiement"
  - "groupes de disponibilité [SQL Server], point de terminaison"
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
caps.latest.revision: 9
ms.author: "mikeray"
manager: "jhubbard"
---
# Cr&#233;er un point de terminaison de mise en miroir de bases de donn&#233;es pour les groupes de disponibilit&#233; Always On (SQL Server PowerShell)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment créer un point de terminaison de mise en miroir de bases de données à utiliser par [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de PowerShell.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour créer un point de terminaison de mise en miroir de bases de données, à l'aide de :**  [PowerShell](#PowerShellProcedure)  
  
## Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
> [!IMPORTANT]  
>  L'algorithme RC4 est déconseillé. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Nous vous recommandons d'utiliser AES.  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CREATE ENDPOINT ou l'appartenance au rôle serveur fixe sysadmin. Pour plus d’informations, consultez [Autorisations de point de terminaison GRANT &#40;Transact-SQL&#41;](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour créer un point de terminaison pour la mise en miroir de bases de données**  
  
1.  Remplacez le répertoire (**cd**) par l’instance de serveur pour laquelle vous voulez créer le point de terminaison de mise en miroir de bases de données.  
  
2.  Utilisez l’applet de commande **New-SqlHadrEndpoint** pour créer le point de terminaison, puis **Set-SqlHadrEndpoint** pour démarrer le point de terminaison.  
  
###  <a name="PShellExample"></a> Exemple (PowerShell)  
 Les commandes PowerShell suivantes créent un point de terminaison de mise en miroir de bases de données sur une instance de SQL Server (*Machine*\\*Instance*). Le point de terminaison utilise le port 5022.  
  
> [!IMPORTANT]  
>  Cet exemple fonctionne uniquement sur une instance de serveur à laquelle aucun point de terminaison de mise en miroir de bases de données n'est actuellement associé.  
  
```  
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"  
  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour configurer un point de terminaison de mise en miroir de bases de données**  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database mirroring - use certificates for outbound connections.md)  
  
    -   [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions entrantes &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database mirroring - use certificates for inbound connections.md)  
  
-   [Spécifier une adresse réseau de serveur &#40;mise en miroir de bases de données&#41;](../../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
 **Pour afficher des informations sur le point de terminaison de mise en miroir de bases de données**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
## Voir aussi  
 [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)   
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  