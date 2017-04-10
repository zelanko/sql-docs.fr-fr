---
title: "R&#233;f&#233;rence PowerShell Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# R&#233;f&#233;rence PowerShell Analysis Services
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inclut un fournisseur PowerShell (SQLAS) et des applets de commande (SQLASCMDLETS) afin que vous puissiez utiliser Windows PowerShell pour parcourir, administrer et interroger des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d'informations sur le chargement et l'utilisation du fournisseur et des applets de commande, consultez [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md). Pour un exemple d’utilisation des types AMO dans PowerShell afin de créer une base de données tabulaire, voir [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md).  
  
##  <a name="bkmk_cmdlets"></a> Applets de commande Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit des applets de commande correspondant aux méthodes indiquées dans l’espace de noms **Microsoft.AnalysisServices**. Le tableau suivant décrit chaque applet de commande et fournit un lien vers la méthode AMO correspondante.  
  
 Si vous souhaitez utiliser PowerShell pour effectuer une tâche qui n’est pas représentée dans la liste suivante (par exemple, pour créer ou synchroniser une base de données), vous pouvez écrire le script TMSL ou XMLA de cette action, puis l’exécuter à l’aide de l’applet de commande **Invoke-ASCmd**.  
  
|Applet de commande|Description|Méthodes AMO équivalentes|  
|------------|-----------------|----------------------------|  
|[Applet de commande Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)|Ajoutez un membre à un rôle de base de données.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Applet de commande Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Sauvegardez une base de données Analysis Services.|<xref:Microsoft.AnalysisServices.Database.Backup%2A>|  
|[Applet de commande Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|Exécutez une requête ou un script au format XMLA ou TSML (JSON).|<xref:Microsoft.AnalysisServices.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|Traitez une base de données.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Applet de commande Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|Traitez un cube.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Applet de commande Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|Traitez une dimension.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Applet de commande Invoke-ProcessPartition](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|Traitez une partition.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Applet de commande Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|Traitez une table dans un modèle tabulaire, un modèle de compatibilité 1200 ou une version ultérieure.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Applet de commande Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)|Fusionnez une partition.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[Applet de commande New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|Créer un dossier pour contenir une sauvegarde de base de données.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[Applet de commande New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|Spécifier un ou plusieurs serveurs distants sur lesquels restaurer la base de données.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Applet de commande Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|Supprimer un membre d'un rôle de base de données.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Applet de commande Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|Restaurer une base de données sur une instance de serveur.|<xref:Microsoft.AnalysisServices.Server.Restore%2A>|  
  
## Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Langage de script Analysis Services &#40;ASSL pour XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)  
  
  