---
title: Créer une base de données mise en miroir de point de terminaison pour les groupes de disponibilité AlwaysOn (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 77df7902f5dd1673736f4a993c4e29c50d7accc0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62814665"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a>Créer un point de terminaison de mise en miroir de bases de données pour les groupes de disponibilité AlwaysOn (SQL Server PowerShell)
  Cette rubrique explique comment créer un point de terminaison de mise en miroir de bases de données à utiliser par [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de PowerShell.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour créer un point de terminaison de mise en miroir de bases de données à l’aide de**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
> [!IMPORTANT]  
>  L'algorithme RC4 est déconseillé. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Nous vous recommandons d'utiliser AES.  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CREATE ENDPOINT ou l'appartenance au rôle serveur fixe sysadmin. Pour plus d’informations, consultez [Autorisations de point de terminaison GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
 **Pour créer un point de terminaison pour la mise en miroir de bases de données**  
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur pour laquelle vous voulez créer le point de terminaison de mise en miroir de bases de données.  
  
2.  Utilisez l'applet de commande `New-SqlHadrEndpoint` pour créer le point de terminaison, puis utilisez `Set-SqlHadrEndpoint` pour démarrer le point de terminaison.  
  
###  <a name="PShellExample"></a> Exemple (PowerShell)  
 Les commandes PowerShell suivantes créent un point de terminaison de mise en miroir de bases de données sur une instance de SQL Server (*Machine*\\*Instance*). Le point de terminaison utilise le port 5022.  
  
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
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions sortantes &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Autoriser un point de terminaison de mise en miroir de bases de données à utiliser des certificats pour les connexions entrantes &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Spécifier une adresse réseau de serveur &#40;mise en miroir de bases de données&#41;](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Pour afficher des informations sur le point de terminaison de mise en miroir de bases de données**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)   
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
