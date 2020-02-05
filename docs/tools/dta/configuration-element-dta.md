---
title: Configuration, élément (Assistant Paramétrage de base de données)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 79073bca20afa853c1b6fbf548ed804f71f074fe
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307983"
---
# <a name="configuration-element-dta"></a>Configuration, élément (Assistant Paramétrage de base de données)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
|**SpecificationMode**|facultatif. Spécifie si l'Assistant Paramétrage du moteur de base de données doit analyser la configuration spécifiée en relation avec la configuration existante active ou comme une configuration autonome entièrement nouvelle. Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :<br /><br /> **Relative**:<br />                  Évalue la configuration spécifiée en relation avec la configuration existante active des structures PDS (index, vues indexées, partitions) dans la base de données en cours de paramétrage. Par exemple :<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  Évalue la configuration spécifiée comme une configuration autonome. Lorsque la valeur Absolute est spécifiée, l'Assistant Paramétrage du moteur de base de données ne prend pas en compte la configuration existante. Par exemple :<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|facultatif. Peut être utilisé une seule fois pour chaque élément **DTAInput** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Éléments enfants**|[Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
