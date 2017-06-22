---
title: "Configurer les paramètres de propriété HealthCheckTimeout | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fe45e057f3e8a9a4cd105cad16ef773c2aed0928
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="configure-healthchecktimeout-property-settings"></a>Configurer les paramètres de propriété HealthCheckTimeout
  Le paramètre HealthCheckTimeout est utilisé pour spécifier le temps, en millisecondes, pendant lequel la DLL de ressource SQL Server doit attendre les informations retournées par la procédure stockée [sp_server_diagnostics](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) avant de déclarer l’instance de cluster de basculement Always On comme sans réponse. Les modifications apportées aux paramètres de délai d'attente entrent immédiatement en vigueur et ne requièrent pas de redémarrage de la ressource SQL Server.  
  
-   **Before you begin:**  [Limitations and Restrictions](#Limits), [Security](#Security)  
  
-   **To Configure the HeathCheckTimeout setting, using:**  [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Limits"></a> Limitations et restrictions  
 La valeur par défaut de cette propriété est 30 000 millisecondes (30 secondes). La valeur minimale est 15 000 millisecondes (15 secondes).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite les autorisations ALTER SETTINGS et VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>Pour configurer les paramètres HealthCheckTimeout  
  
1.  Démarrez Windows PowerShell avec élévation de privilèges via **Exécuter en tant qu'administrateur**.  
  
2.  Importez le module **FailoverClusters** pour activer les applets de commande de cluster.  
  
3.  Utilisez l’applet de commande **Get-ClusterResource** pour rechercher la ressource [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , puis utilisez l’applet de commande **Set-ClusterParameter** pour définir la propriété **HealthCheckTimeout** pour l’instance de cluster de basculement.  
  
> [!TIP]  
>  Chaque fois que vous ouvrez une nouvelle fenêtre PowerShell, vous devez importer le module **FailoverClusters** .  
  
### <a name="example-powershell"></a>Exemple (PowerShell)  
 L'exemple suivant modifie le paramètre HealthCheckTimeout sur la ressource [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» afin qu'il indique 60 000 millisecondes.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>Contenu connexe (PowerShell)  
  
-   [Clustering and High-Availability](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering et haute disponibilité) (Blog de l’équipe de clustering de basculement et d’équilibrage de la charge réseau)  
  
-   [Mise en route de Windows PowerShell sur un cluster de basculement](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Commandes de ressource de cluster et applets de commande Windows PowerShell équivalentes](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Utilisation du composant logiciel enfichable Gestionnaire du cluster de basculement  
 **Pour configurer le paramètre HeathCheckTimeout**  
  
1.  Ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement.  
  
2.  Développez **Services et applications** et sélectionnez l'instance FCI.  
  
3.  Cliquez avec le bouton droit sur **Ressource SQL Server** sous **Autres ressources** , puis sélectionnez **Propriétés** dans le menu contextuel. La boîte de dialogue **Propriétés** de la ressource SQL Server s'ouvre.  
  
4.  Sélectionnez l'onglet **Propriétés** , entrez la valeur souhaitée pour la propriété **HealthCheckTimeout** , puis cliquez sur **OK** pour appliquer la modification.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 À l’aide de l’instruction [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md) [!INCLUDE[tsql](../../../includes/tsql-md.md)], spécifiez la valeur de la propriété HealthCheckTimeOut.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant définit l'option HealthCheckTimeout sur 15 000 millisecondes (15 secondes).  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Stratégie de basculement pour les instances de cluster de basculement](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  

