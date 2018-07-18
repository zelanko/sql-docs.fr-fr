---
title: Référence PowerShell Analysis Services | Microsoft Docs
ms.date: 06/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13ea15a23bbf6de6c50b494f709f65cae2f7c48b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992901"
---
# <a name="analysis-services-powershell-reference"></a>Référence PowerShell Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Applets de commande PowerShell sont inclus dans le [module SqlServer](https://www.powershellgallery.com/packages/SqlServer/21.0.17099). 
  
>[!NOTE] 
> Opérations de base de données Azure Analysis Services utilisent le même module SqlServer que SQL Server Analysis Services. Toutefois, pas toutes les applets de commande sont pris en charge pour Azure Analysis Services. Pour plus d’informations, consultez [gérer Azure Analysis Services avec PowerShell](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell).
  
##  <a name="bkmk_cmdlets"></a> Applets de commande Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit des applets de commande correspondant aux méthodes indiquées dans l’espace de noms **Microsoft.AnalysisServices** . Le tableau suivant décrit chaque applet de commande et fournit un lien vers la méthode AMO correspondante.  
  
 Si vous souhaitez utiliser PowerShell pour effectuer une tâche qui n’est pas représentée dans la liste suivante (par exemple, pour créer ou synchroniser une base de données), vous pouvez écrire le script TMSL ou XMLA de cette action, puis l’exécuter à l’aide de l’applet de commande **Invoke-ASCmd** .  
  
|Applet de commande|Description|Méthodes AMO équivalentes|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/Add-RoleMember)|Ajoutez un membre à un rôle de base de données.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Backup-ASDatabase, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/backup-asdatabase)|Sauvegardez une base de données Analysis Services.|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Invoke-ASCmd, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/invoke-ascmd)|Exécutez une requête ou un script au format XMLA ou TSML (JSON).|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processasdatabase)|Traitez une base de données.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessCube, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processcube)|Traitez un cube.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessDimension, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processdimension)|Traitez une dimension.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessPartition, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processpartition)|Traitez une partition.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessTable, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processtable)|Traiter une table dans un modèle tabulaire, le modèle de compatibilité 1200 ou supérieur.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Merge-Partition, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/merge-partition)|Fusionnez une partition.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[New-RestoreFolder, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/new-restorefolder)|Créer un dossier pour contenir une sauvegarde de base de données.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[New-RestoreLocation, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/new-restorelocation)|Spécifier un ou plusieurs serveurs distants sur lesquels restaurer la base de données.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Remove-RoleMember, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/remove-rolemember)|Supprimer un membre d'un rôle de base de données.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Restore-ASDatabase, applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/restore-asdatabase)|Restaurer une base de données sur une instance de serveur.|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
