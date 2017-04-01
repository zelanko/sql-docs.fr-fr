---
title: "Supprimer une instance de SQL&#160;Server de l&#39;utilitaire SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.utility.remove.f1"
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Supprimer une instance de SQL&#160;Server de l&#39;utilitaire SQL&#160;Server
  Suivez la procédure suivante pour supprimer une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette procédure supprime l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du mode Liste de l’UCP et interrompt la collecte de données de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas désinstallée.  
  
> [!IMPORTANT]  
>  Avant d'utiliser cette procédure pour supprimer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assurez-vous que les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Agent SQL Server s'exécutent sur l'instance à supprimer.  
  
1.  Depuis l’Explorateur de l’utilitaire dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Instances gérées**. Observez le mode Liste des instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le volet de contenu de l’Explorateur de l’utilitaire.  
  
2.  Dans la colonne **Nom de l’instance SQL Server** du mode Liste, sélectionnez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à supprimer de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cliquez avec le bouton droit sur l’instance à supprimer et sélectionnez **Supprimer une instance gérée**.  
  
3.  Spécifiez des informations d’identification avec des privilèges d’administrateur pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : cliquez sur **Se connecter**, vérifiez les informations dans la boîte de dialogue **Se connecter au serveur**, puis cliquez sur **Se connecter**. Les informations de connexion s’affichent sur le dialogue **Supprimer une instance gérée**.  
  
4.  Cliquez sur **OK** pour confirmer l’opération. Pour quitter l’installation, cliquez sur **Annuler**.  
  
## Supprimer manuellement une instance gérée de SQL Server d'un utilitaire SQL Server  
 Cette procédure supprime l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du mode Liste de l’UCP et interrompt la collecte de données de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas désinstallée.  
  
 Pour utiliser PowerShell pour supprimer une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce script effectue les opérations suivantes :  
  
-   obtient l'UCP par le nom de l'instance du serveur ;  
  
-   supprime l’instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object –Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
 Notez qu'il est important de désigner l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par son nom exact, tel qu'il est enregistré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sensible à la casse, vous devez spécifier le nom de l'instance en respectant la casse exacte, telle qu'elle est retournée par @@SERVERNAME. Pour obtenir le nom de l'instance pour l'instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez la requête suivante sur l'instance gérée :  
  
```  
select @@SERVERNAME AS instance_name  
```  
  
 À ce stade, l’instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est complètement supprimée de l’UCP. Elle disparaît du mode Liste lorsque vous actualisez les données de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le résultat est identique à celui qu'obtient un utilisateur qui effectue avec succès l'opération de suppression d'instance gérée dans l'interface utilisateur SSMS.  
  
## Voir aussi  
 [Utiliser l'Explorateur de l'utilitaire pour gérer l'Utilitaire SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Résolution des problèmes liés à l'utilitaire SQL Server](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  