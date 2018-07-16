---
title: Élément de configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0383bc1c8bef5a84b77c8b63fb424995a2181ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241749"
---
# <a name="configuration-element-dta"></a>Configuration, élément (Assistant Paramétrage de base de données)
  Spécifie une configuration spécifiée par l'utilisateur se composant de structures PDS existantes et hypothétiques en vue d'être analysée par l'Assistant Paramétrage du moteur de base de données lors du paramétrage d'une charge de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut de configuration|Description|  
|-----------------------------|-----------------|  
|`SpecificationMode`|Facultatif. Spécifie si l'Assistant Paramétrage du moteur de base de données doit analyser la configuration spécifiée en relation avec la configuration existante active ou comme une configuration autonome entièrement nouvelle. Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :<br /><br /> `Relative` : <br />                  Évalue la configuration spécifiée en relation avec la configuration existante active des structures PDS (index, vues indexées, partitions) dans la base de données en cours de paramétrage. Exemple : <br />`<Configuration SpecificationMode="Relative">`<br /><br /> `Absolute` : <br />                  Évalue la configuration spécifiée comme une configuration autonome. Lorsque la valeur Absolute est spécifiée, l'Assistant Paramétrage du moteur de base de données ne prend pas en compte la configuration existante. Exemple :<br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Peut utiliser qu’une seule fois pour chaque `DTAInput` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Éléments enfants**|[Élément de serveur de Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
