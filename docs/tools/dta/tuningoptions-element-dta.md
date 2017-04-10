---
title: "TuningOptions, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "TuningOptions (élément)"
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# TuningOptions, &#233;l&#233;ment (Assistant Param&#233;trage de base de donn&#233;es)
  Contient les options de paramétrage pour une session de paramétrage spécifique.  
  
## Syntaxe  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Si cet élément est utilisé, il ne peut être utilisé qu'une seule fois pour l'élément **DTAInput** .|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Éléments enfants**|Élément**ReportSet** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**TuningLogTable** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**NumberOfEvents** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin, élément &#40;DTA&#41;](../../tools/dta/tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB, élément &#40;DTA&#41;](../../tools/dta/storageboundinmb-element-dta.md)<br /><br /> Élément**MaxKeyColumnsInIndex** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**MaxColumnsInIndex** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**MinPercentageImprovement** . Pour plus d'informations, consultez le [schéma XML de l'Assistant Paramétrage du moteur de base de données](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TestServer, élément &#40;DTA&#41;](../../tools/dta/testserver-element-dta.md)<br /><br /> [FeatureSet, élément &#40;DTA&#41;](../../tools/dta/featureset-element-dta.md)<br /><br /> [Partitioning, élément &#40;DTA&#41;](../../tools/dta/partitioning-element-dta.md)<br /><br /> [DropOnlyMode, élément &#40;DTA&#41;](../../tools/dta/droponlymode-element-dta.md)<br /><br /> [KeepExisting, élément &#40;DTA&#41;](../../tools/dta/keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation, élément &#40;DTA&#41;](../../tools/dta/onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect, élément &#40;DTA&#41;](../../tools/dta/databasetoconnect-element-dta.md)<br /><br /> Élément**IgnoreConstantsInWorkload** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**RetainShellDB** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## Exemple  
 Pour obtenir des exemples de l’élément **TuningOptions**, consultez les [exemples de fichiers d’entrée XML &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  