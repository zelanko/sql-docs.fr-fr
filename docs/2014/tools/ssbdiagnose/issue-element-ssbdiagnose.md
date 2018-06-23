---
title: Élément issue (ssbdiagnose) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: adff003b1d6b98d7778311b84aca4666dd802d27
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142614"
---
# <a name="issue-element-ssbdiagnose"></a>Élément Issue (ssbdiagnose)
  Signale un problème identifié par l’utilitaire **ssbdiagnose** . Le fichier de sortie XML de **ssbdiagnose** comporte un élément Issue par problème signalé.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribute|Description|  
|---------------|-----------------|  
|`type`|Identifie la catégorie de problème signalée par l’élément Issue :<br /><br /> **« Diagnosis »** Signale un problème de configuration identifié lors de l'analyse d'une configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **« Problem »** Signale un problème qui a empêché **ssbdiagnose** d’effectuer son analyse. Résolvez le problème et exécutez de nouveau **ssbdiagnose**.<br /><br /> **« Event »** Signale un événement [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] identifié lors de l’exécution d’une vérification **-RUNTIME** . Les événements sont signalés uniquement si **-SHOWEVENTS** est spécifié.|  
|`code`|Identifie le numéro d'erreur du message.|  
|`server`|Identifie l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans laquelle le problème a été trouvé. Si le problème a été identifié dans une instance par défaut, l'attribut de serveur porte uniquement le nom de l'ordinateur. Si le problème a été identifié dans une instance nommée, l'attribut de serveur prend la forme NomOrdinateur\NomInstance.|  
|`database`|Identifie le nom de la base de données dans laquelle le problème a été trouvé.|  
|`object`|Identifie le nom de l'objet dans lequel le problème a été trouvé. Si le problème était un problème de niveau instance ou base de données, l'attribut de l'objet répète le nom de l'instance ou de la base de données.|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`string`, longueur est illimitée.|  
|**Value**|Retourne le texte du message d'erreur.|  
|**Occurrence**|Une fois par erreur signalée.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DiagnosticInformation Élément &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**Éléments enfants**|None|  
  
## <a name="example"></a>Exemple  
 Cet élément signale une erreur 1102 pour une base de données ne possédant pas de clé principale, où l'erreur a été détectée lors de l'analyse d'une configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)] .  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  