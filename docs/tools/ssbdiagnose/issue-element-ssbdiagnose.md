---
title: "&#201;l&#233;ment Issue (ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "issue, élément"
  - "Format du fichier de sortie XML [ssbdiagnose], élément Issue"
  - "ssbdiagnose"
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# &#201;l&#233;ment Issue (ssbdiagnose)
  Signale un problème identifié par l’utilitaire **ssbdiagnose** . Le fichier de sortie XML de **ssbdiagnose** comporte un élément Issue par problème signalé.  
  
## Syntaxe  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**type**|Identifie la catégorie de problème signalée par l’élément Issue :<br /><br /> **« Diagnosis »** Signale un problème de configuration identifié lors de l'analyse d'une configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **« Problem »** Signale un problème qui a empêché **ssbdiagnose** d’effectuer son analyse. Résolvez le problème et exécutez de nouveau **ssbdiagnose**.<br /><br /> **« Event »** Signale un événement [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] identifié lors de l’exécution d’une vérification **-RUNTIME**. Les événements sont signalés uniquement si **-SHOWEVENTS** est spécifié.|  
|**code**|Identifie le numéro d'erreur du message.|  
|**server**|Identifie l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans laquelle le problème a été trouvé. Si le problème a été identifié dans une instance par défaut, l'attribut de serveur porte uniquement le nom de l'ordinateur. Si le problème a été identifié dans une instance nommée, l'attribut de serveur prend la forme NomOrdinateur\NomInstance.|  
|**database**|Identifie le nom de la base de données dans laquelle le problème a été trouvé.|  
|**objet**|Identifie le nom de l'objet dans lequel le problème a été trouvé. Si le problème était un problème de niveau instance ou base de données, l'attribut de l'objet répète le nom de l'instance ou de la base de données.|  
  
## Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, longueur illimitée.|  
|**Valeur**|Retourne le texte du message d'erreur.|  
|**Occurrence**|Une fois par erreur signalée.|  
  
## Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Éléments enfants**|Aucune|  
  
## Exemple  
 Cet élément signale une erreur 1102 pour une base de données ne possédant pas de clé principale, où l'erreur a été détectée lors de l'analyse d'une configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  