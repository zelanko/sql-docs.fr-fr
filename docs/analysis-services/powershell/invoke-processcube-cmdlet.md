---
title: "Applet de commande Invoke-ProcessCube | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b10ba7c1-8f10-4e72-9626-f9285e4341fd
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Applet de commande Invoke-ProcessCube
  Traitez un cube en utilisant une variable de type de traitement spécifique.  
  
## Syntaxe  
 `Invoke-ProcessCube [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessCube –DatabaseCube <Microsoft.AnalysisServices.Cube> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## Description  
 L'applet de commande Invoke-ProcessCube traite un cube au niveau que vous spécifiez. Par exemple, ProcessFull remplace les données existantes par toutes les nouvelles données. Lors du traitement d'un cube, vous devez spécifier le type de traitement. Pour plus d’informations, consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## Paramètres  
  
### -Name \<string>  
 Spécifie le cube à traiter.  
  
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
  
### -ProcessType \<Microsoft.AnalysisServices.ProcessType>  
 Spécifie le type de processus : ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, ProcessRecalc.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DatabaseCube \<Microsoft.AnalysisSevices.Cube>  
 Spécifie un objet Microsoft.AnalysisServices.Cube à traiter. Utilisez ce paramètre si vous souhaitez transmettre le nom de cube via le pipeline.  
  
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
|Entrées|Aucun|  
|Sorties|Aucun|  
  
## Exemple 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works > Get-Item .| Invoke-ProcessCube–ProcessType:ProcessDefault`  
  
 Cette commande fournit l'identité du cube à traiter.  
  
## Exemple 2  
 `PS SQL SERVER:\sqlas\locahost\default > Invoke-ProcessCube “Adventure Works” –database AWTEST –ProcessType:ProcessDefault`  
  
 Cette commande traite le cube Adventure Works dans la base de données AWTEST.  
  
## Voir aussi  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  