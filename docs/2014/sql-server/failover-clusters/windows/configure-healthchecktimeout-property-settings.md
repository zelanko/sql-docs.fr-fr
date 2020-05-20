---
title: Configurer les paramètres de propriété HealthCheckTimeout | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 435aa6a89b1b7aafd243efbc6de86bcb8f731346
ms.sourcegitcommit: 5a9ec5e28543f106bf9e7aa30dd0a726bb750e25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82925012"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Configurer les paramètres de propriété HealthCheckTimeout
  Le paramètre HealthCheckTimeout est utilisé pour spécifier le temps, en millisecondes, pendant lequel la DLL de ressource SQL Server doit attendre les informations retournées par la procédure stockée [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) avant de déclarer l'instance de cluster de basculement (FCI) AlwaysOn comme sans réponse. Les modifications apportées aux paramètres de délai d'attente entrent immédiatement en vigueur et ne requièrent pas de redémarrage de la ressource SQL Server.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Limits), [Sécurité](#Security)  
  
-   **Pour configurer le paramètre HeathCheckTimeout, utilisez :**  [PowerShell](#PowerShellProcedure), [Gestionnaire du cluster de basculement](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> Limitations et restrictions  
 La valeur par défaut pour cette propriété est 60 000 millisecondes (60 secondes). La valeur minimale est 15 000 millisecondes (15 secondes).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite les autorisations ALTER SETTINGS et VIEW SERVER STATE.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
### <a name="to-configure-healthchecktimeout-settings"></a>Pour configurer les paramètres HealthCheckTimeout  
  
1.  Démarrez Windows PowerShell avec élévation de privilèges via **Exécuter en tant qu'administrateur**.  
  
2.  Importez le module `FailoverClusters` pour activer les applets de commande de cluster.  
  
3.  Utilisez l' `Get-ClusterResource` applet de commande pour rechercher la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ressource, puis utilisez l' `Set-ClusterParameter` applet de commande pour définir la propriété **HealthCheckTimeout** de l’instance de cluster de basculement.  
  
> [!TIP]  
>  Chaque fois que vous ouvrez une nouvelle fenêtre PowerShell, vous devez importer le module `FailoverClusters`.  

 L'exemple suivant modifie le paramètre HealthCheckTimeout sur la ressource [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» afin qu'il indique 60 000 millisecondes.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a>Contenu connexe (PowerShell)  
  
-   [Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Clustering et haute disponibilité) (Blog de l’équipe de clustering de basculement et d’équilibrage de la charge réseau)  
  
-   [Mise en route de Windows PowerShell sur un cluster de basculement](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Commandes de ressource de cluster et applets de commande Windows PowerShell équivalentes](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Utilisation du composant logiciel enfichable Gestionnaire du cluster de basculement  
 **Pour configurer le paramètre HeathCheckTimeout**  
  
1.  Ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement.  
  
2.  Développez **Services et applications** et sélectionnez l'instance FCI.  
  
3.  Cliquez avec le bouton droit sur **Ressource SQL Server** sous **Autres ressources** , puis sélectionnez **Propriétés** dans le menu contextuel. La boîte de dialogue **Propriétés** de la ressource SQL Server s'ouvre.  
  
4.  Sélectionnez l'onglet **Propriétés** , entrez la valeur souhaitée pour la propriété **HealthCheckTimeout** , puis cliquez sur **OK** pour appliquer la modification.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 À l’aide de l’instruction [ALTER Server Configuration](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] , vous pouvez spécifier la valeur de la propriété HealthCheckTimeOut.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant définit l'option HealthCheckTimeout sur 15 000 millisecondes (15 secondes).  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Stratégie de basculement pour les instances de cluster de basculement](failover-policy-for-failover-cluster-instances.md)  
