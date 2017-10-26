---
title: "Traitement par lots d’élément (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Batch Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords:
- Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 72ba969247e7e6ff86013c1c875f4486884268c5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="batch-element-xmla"></a>Élément Batch (XMLA)
  Effectue XML d’un ou plusieurs pour les commandes Analysis (XMLA) comme un traitement par lots, dans l’ordre ou en parallèle, sur une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Liaisons](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md), [DataSourceView](../../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md), [parallèle](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)<br /><br /> Un ou plusieurs des commandes XMLA suivantes : [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), [créer](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md), [supprimer](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [supprimer](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [insérer](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [verrou](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [processus](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [Instruction](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md), [s’abonner](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md), [déverrouiller](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md), [mise à jour](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribut| Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Facultatif **Boolean** attribut) indique si tous les objets qui nécessitent un nouveau seront traités.<br /><br /> Si la valeur true, le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance traite tous les objets qui nécessitent un nouveau traitement suite au traitement d’un objet inclus dans le **lot** commande.<br /><br /> Si la valeur **false**, le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance traite uniquement les objets inclus dans le **lot** commande.|  
|Transaction|(Facultatif **booléenne** attribut) indique si la commande est inclus dans le **lot** commande sont traités comme une transaction unique ou des transactions individuelles.<br /><br /> Si défini sur true, toutes les commandes incluses dans le **lot** commande sont considérées comme une transaction unique. Si la commande échoue, les commandes exécutées avant la commande défaillante sont restaurées et la **lot** commande arrête sans exécuter les commandes suivantes.<br /><br /> Si la valeur **false**, le **lot** commande tente de s’exécuter toutes les commandes et valide les résultats de chaque commande se termine correctement.|  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]  
>  Command/Execute/Statement n'est pas pris en charge dans une opération de traitement par lots.  
  
 Pour plus d’informations sur l’exécution d’opérations par lots en XMLA, consultez [exécution d’opérations de traitement par lots &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

