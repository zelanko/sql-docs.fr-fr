---
title: "Applet de commande Invoke-ProcessPartition | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 516fab44-734e-425b-9bd0-b4aee1fd338f
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Applet de commande Invoke-ProcessPartition
  Traitez une partition en utilisant une variable de type de traitement spécifique.  
  
## Syntaxe  
 `Invoke-ProcessPartition [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [-CubeName] <System.String> [-MeasureGroupName] <System.String> [<CommonParameters>]`  
  
 `Invoke-ProcessPartition –DatabasePartition <Microsoft.AnalysisServices.Partition> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## Description  
 L'applet de commande Invoke-ProcessParition traite une partition spécifique d'une base de données Analysis Services pour un cube et un groupe de mesures donnés. La valeur ProcessType détermine l'étendue de l'opération. Lors du traitement d'une partition, vous devez spécifier le type de traitement. Pour plus d’informations, consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## Paramètres  
  
### -Name \<string>  
 Spécifie la partition à traiter.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Database \<string>  
 Spécifie la base de données à laquelle le cube appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -CubeName \<string>  
 Spécifie le cube auquel le groupe de mesures appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -MeasureGroupName \<string>  
 Spécifie le groupe de mesures auquel la partition appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DatabasePartition \<Microsoft.AnalysisServices.Partition>  
 Spécifie la partition à traiter.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -ProcessType \<Microsoft.AnalysisServices.ProcessType>  
 Spécifie le type de processus : ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, ProcessRecalc.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun|  
|Sorties|Aucun|  
  
## Exemple 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\Sales Orders\Partitions\Total_Orders_2004 > Get-Item .| Invoke-ProcessPartition –ProcessType:ProcessDefault`  
  
 Cette commande fournit l'identité de la partition à traiter.  
  
## Exemple 2  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups> Invoke-ProcessPartition –Name “Total_Orders_2003” –MeasureGroupname “Sales Order” –CubeName “Adventure Works” –database “AWTEST” –ProcessType “ProcessFull”`  
  
 Cette commande traite la partition Total_Orders_2003 dans le groupe de mesures Sales Orders de la base de données AWTEST.  
  
## Voir aussi  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  