---
title: "Applet de commande Invoke-ProcessDimension | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9506938e-7f9f-4595-ad6d-98c8b0ce8395
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Applet de commande Invoke-ProcessDimension
  Traitez une dimension en utilisant une variable de type de traitement spécifique.  
  
## Syntaxe  
 `Invoke-ProcessDimension [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessDimension –DatabaseDimension <Microsoft.AnalysisServices.Dimension> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## Description  
 L'applet de commande Invoke-ProcessDimension traite la dimension spécifiée. Vous devez spécifier le type de traitement. Pour plus d’informations sur le traitement des types d’une dimension, consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## Paramètres  
  
### -Name \<string>  
 Spécifie la dimension à traiter.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Database \<string>  
 Spécifie la base de données à laquelle la dimension appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -ProcessType \<Microsoft.AnalysisServices.ProcessType>  
 Spécifie le type de processus : ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, ProcessRecalc.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DatabaseDimension \<Microsoft.AnalysisSevices.Dimension>  
 Spécifie un objet Microsoft.AnalysisServices.Dimension à traiter. Utilisez ce paramètre si vous souhaitez transmettre le nom de dimension via le pipeline.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|True (ByPropertyName)|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Microsoft.AnalysisSevices.Dimension|  
|Sorties|Aucun|  
  
## Exemple 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Dimensions\Account> Get-Item .| Invoke-ProcessDimension –ProcessType:ProcessDefault`  
  
 Cette commande récupère l'objet de dimension spécifié via le pipeline et le traite.  
  
## Exemple 2  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Dimensions > Invoke-ProcessDimension –Name “Customer” –Database “AWTEST” –ProcessType “ProcessDefault”`  
  
 Cette commande identifie une dimension spécifique qui sera traitée.  
  
> [!NOTE]  
>  Parfois, une dimension traitée correctement apparaît comme « non traitée » lorsque vous répertoriez le dossier des dimensions dans la fenêtre PowerShell. Pour vérifier si une dimension a été réellement traitée, vérifiez les propriétés de dimension dans SQL Server Management Studio.  
  
## Voir aussi  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  