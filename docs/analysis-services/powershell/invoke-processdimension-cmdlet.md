---
title: Applet de commande Invoke-ProcessDimension | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9506938e-7f9f-4595-ad6d-98c8b0ce8395
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8a24a4b19f20e28346456e3c0c53f39eaeb200b9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="invoke-processdimension-cmdlet"></a>Applet de commande Invoke-ProcessDimension
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Traitez une dimension en utilisant une variable de type de traitement spécifique.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="syntax"></a>Syntaxe  
 `Invoke-ProcessDimension [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessDimension –DatabaseDimension <Microsoft.AnalysisServices.Dimension> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a> Description  
 L'applet de commande Invoke-ProcessDimension traite la dimension spécifiée. Vous devez spécifier le type de traitement. Pour plus d’informations sur le traitement des types d’une dimension, consultez [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-name-string"></a>-Name \<string>  
 Spécifie la dimension à traiter.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-database-string"></a>-De base de données \<chaîne >  
 Spécifie la base de données à laquelle la dimension appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-ProcessType \<Microsoft.AnalysisServices.ProcessType>  
 Spécifie le type de processus : ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, ProcessRecalc.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-databasedimension-microsoftanalysissevicesdimension"></a>-DatabaseDimension \<Microsoft.AnalysisSevices.Dimension >  
 Spécifie un objet Microsoft.AnalysisServices.Dimension à traiter. Utilisez ce paramètre si vous souhaitez transmettre le nom de dimension via le pipeline.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|True (ByPropertyName)|  
|Accepter les caractères génériques ?|false|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Microsoft.AnalysisSevices.Dimension|  
|Sorties|Aucun|  
  
## <a name="example-1"></a>Exemple 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Dimensions\Account> Get-Item .| Invoke-ProcessDimension –ProcessType:ProcessDefault`  
  
 Cette commande récupère l'objet de dimension spécifié via le pipeline et le traite.  
  
## <a name="example-2"></a>Exemple 2  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Dimensions > Invoke-ProcessDimension –Name “Customer” –Database “AWTEST” –ProcessType “ProcessDefault”`  
  
 Cette commande identifie une dimension spécifique qui sera traitée.  
  
> [!NOTE]  
>  Parfois, une dimension traitée correctement apparaît comme « non traitée » lorsque vous répertoriez le dossier des dimensions dans la fenêtre PowerShell. Pour vérifier si une dimension a été réellement traitée, vérifiez les propriétés de dimension dans SQL Server Management Studio.  
  
  
  
