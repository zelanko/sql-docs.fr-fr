---
title: Élément TuningOptions (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3050ce285cc98386f6de6278bedd2520cb39ba36
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63061063"
---
# <a name="tuningoptions-element-dta"></a>TuningOptions, élément (Assistant Paramétrage de base de données)
  Contient les options de paramétrage pour une session de paramétrage spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|facultatif. Si cet élément est utilisé, il ne peut être utilisé qu'une seule fois pour l'élément `DTAInput`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Éléments enfants**|`ReportSet`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `TuningLogTable`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `NumberOfEvents`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin, élément &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB, élément &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MaxColumnsInIndex`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MinPercentageImprovement`appartient. Pour plus d'informations, consultez le [schéma XML de l'Assistant Paramétrage du moteur de base de données](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TestServer, élément &#40;DTA&#41;](server-element-dta.md)<br /><br /> [FeatureSet, élément &#40;Assistant Paramétrage de base de données&#41;](featureset-element-dta.md)<br /><br /> [Partitioning, élément &#40;Assistant Paramétrage de base de données&#41;](partitioning-element-dta.md)<br /><br /> [DropOnlyMode, élément &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [KeepExisting, élément &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation, élément &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect, élément &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `RetainShellDB`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Exemple  
 Pour obtenir des exemples `TuningOptions` de l’élément, consultez les [exemples de fichiers d’entrée XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
