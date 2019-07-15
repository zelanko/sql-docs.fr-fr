---
title: Onlineindexoperation, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f852149379edc74e36de09b01a60e0ec73f41fdb
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733513"
---
# <a name="onlineindexoperation-element-dta"></a>OnlineIndexOperation, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Spécifie si les index, les vues indexées ou les partitions recommandées par l'Assistant Paramétrage du moteur de base de données peuvent être créés en ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, aucune longueur maximale.|  
|**Valeurs autorisées**|**OFF**<br /> Aucune PDS ne peut être créée en ligne.<br /><br /> **ON**<br /> Toutes les PDS recommandées peuvent être créées en ligne.<br /><br /> **MIXED**<br /> L'Assistant Paramétrage du moteur de base de données tente de recommander des PDS pouvant être créées en ligne lorsque cela est possible.<br /><br /> Utilisez une de ces valeurs avec cet élément. Si les index sont créés en ligne, le mot clé **ONLINE = ON** est ajouté à sa définition d’objet.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Ne peut être utilisé qu’une seule fois pour l’élément **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
