---
title: Traitement par lots, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Batch Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords:
- Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 269eedd9a48d1bf7bde43d0294bac7a81b9f90ad
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291235"
---
# <a name="batch-element-xmla"></a>Élément Batch (XMLA)
  Effectue XML d’un ou plusieurs pour les commandes Analysis (XMLA) comme une opération de traitement par lots, séquentiellement ou en parallèle, sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Batch Transaction="Boolean" ProcessAffectedObjects="Boolean">  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <Parallel>...</Parallel>  
      <!-- One or more XMLA commands -->  
   </Batch>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Liaisons](../xml-elements-properties/bindings-element-xmla.md), [DataSource](../xml-elements-properties/source-element-xmla.md), [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../scripting/objects/errorconfiguration-element-assl.md), [parallèles](../xml-elements-properties/parallel-element-xmla.md)<br /><br /> Un ou plusieurs des commandes XMLA suivantes : [Alter](alter-element-xmla.md), [sauvegarde](backup-element-xmla.md), [BeginTransaction](begintransaction-element-xmla.md), [ClearCache](clearcache-element-xmla.md), [ CommitTransaction](committransaction-element-xmla.md), [créer](create-element-xmla.md), [supprimer](delete-element-xmla.md), [DesignAggregations](designaggregations-element-xmla.md), [Drop](drop-element-xmla.md), [Insérer](insert-element-xmla.md), [verrou](lock-element-xmla.md), [MergePartitions](mergepartitions-element-xmla.md), [NotifyTableChange](notifytablechange-element-xmla.md), [processus](process-element-xmla.md), [Restaurer](restore-element-xmla.md), [RollbackTransaction](rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [instruction](statement-element-xmla.md), [s’abonner](subscribe-element-xmla.md), [Synchroniser](synchronize-element-xmla.md), [déverrouiller](unlock-element-xmla.md), [mise à jour](update-element-xmla.md), [UpdateCells](drop-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Attribut `Boolean` facultatif) Indique si tous les objets qui exigent un nouveau traitement seront traités.<br /><br /> S'il possède la valeur True, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] traite tous les objets qui nécessitent un nouveau traitement suite au traitement d'un objet inclus dans la commande `Batch`.<br /><br /> Si l'attribut possède la valeur `false`, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] traite uniquement les objets inclus dans la commande `Batch`.|  
|Transaction|(Attribut `Boolean` facultatif) Indique si les commandes incluses dans la commande `Batch` sont traitées comme une transaction unique ou en tant que transactions individuelles.<br /><br /> S'il possède la valeur True, toutes les commandes incluses dans la commande `Batch` sont considérées comme une transaction unique. En cas d'échec d'une commande, les commandes exécutées avant la commande défaillante sont restaurées, et la commande `Batch` s'arrête sans exécuter les commandes suivantes.<br /><br /> Si l'attribut possède la valeur `false`, la commande `Batch` tente d'exécuter toutes les commandes et valide les résultats de chaque commande effectuée avec succès.|  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]  
>  Command/Execute/Statement n'est pas pris en charge dans une opération de traitement par lots.  
  
 Pour plus d’informations sur l’exécution d’opérations par lots en XMLA, consultez [exécution d’opérations de traitement par lots &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
