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
ms.openlocfilehash: acb2a812f2e3c29a56916c671d76d91c676272d6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53359612"
---
# <a name="configure-healthchecktimeout-property-settings"></a>Configurer les paramètres de propriété HealthCheckTimeout
  Le paramètre HealthCheckTimeout est utilisé pour spécifier le temps, en millisecondes, pendant lequel la DLL de ressource SQL Server doit attendre les informations retournées par la procédure stockée [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) avant de déclarer l'instance de cluster de basculement (FCI) AlwaysOn comme sans réponse. Les modifications apportées aux paramètres de délai d'attente entrent immédiatement en vigueur et ne requièrent pas de redémarrage de la ressource SQL Server.  
  
-   **Avant de commencer :**  [Limitations et Restrictions](#Limits), [sécurité](#Security)  
  
-   **Pour configurer le paramètre HeathCheckTimeout, utilisez :**  [PowerShell](#PowerShellProcedure), [Gestionnaire du Cluster de basculement](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Limits"></a> Limitations et restrictions  
 La valeur par défaut pour cette propriété est 60 000 millisecondes (60 secondes). La valeur minimale est 15 000 millisecondes (15 secondes).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite les autorisations ALTER SETTINGS et VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>Pour configurer les paramètres HealthCheckTimeout  
  
1.  Démarrez Windows PowerShell avec élévation de privilèges via **Exécuter en tant qu'administrateur**.  
  
2.  Importez le module `FailoverClusters` pour activer les applets de commande de cluster.  
  
3.  Utiliser le `Get-ClusterResource` applet de commande pour rechercher la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ressource, puis utiliser `Set-ClusterParameter` applet de commande pour définir le **HealthCheckTimeout** propriété pour l’instance de cluster de basculement.  
  
> [!TIP]  
>  Chaque fois que vous ouvrez une nouvelle fenêtre PowerShell, vous devez importer le module `FailoverClusters`.  
  
### <a name="example-powershell"></a>Exemple (PowerShell)  
 L'exemple suivant modifie le paramètre HealthCheckTimeout sur la ressource [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» afin qu'il indique 60 000 millisecondes.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>Contenu connexe (PowerShell)  
  
-   [Clustering and High-Availability](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (Clustering et haute disponibilité) (Blog de l’équipe de clustering de basculement et d’équilibrage de la charge réseau)  
  
-   [Mise en route de Windows PowerShell sur un cluster de basculement](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Commandes de ressource de cluster et applets de commande Windows PowerShell équivalentes](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Utilisation du composant logiciel enfichable Gestionnaire du cluster de basculement  
 **Pour configurer le paramètre HeathCheckTimeout**  
  
1.  Ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement.  
  
2.  Développez **Services et applications** et sélectionnez l'instance FCI.  
  
3.  Cliquez avec le bouton droit sur **Ressource SQL Server** sous **Autres ressources** , puis sélectionnez **Propriétés** dans le menu contextuel. La boîte de dialogue **Propriétés** de la ressource SQL Server s'ouvre.  
  
4.  Sélectionnez l'onglet **Propriétés** , entrez la valeur souhaitée pour la propriété **HealthCheckTimeout** , puis cliquez sur **OK** pour appliquer la modification.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 À l’aide de l’instruction [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)], spécifiez la valeur de la propriété HealthCheckTimeOut.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant définit l'option HealthCheckTimeout sur 15 000 millisecondes (15 secondes).  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Stratégie de basculement pour les instances de cluster de basculement](failover-policy-for-failover-cluster-instances.md)  
  
  
