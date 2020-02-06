---
title: DTAInput, élément (Assistant Paramétrage de base de données)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 6801f3d8ce45ba41d24d1062ad9979e80e76b38a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307715"
---
# <a name="dtainput-element-dta"></a>DTAInput, élément (Assistant Paramétrage de base de données)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Contient la définition de l'entrée XML pour l'Assistant Paramétrage du moteur de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristiques|Description|  
|---------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par élément **DTAXML** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAXML, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**Éléments enfants**|[Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Workload, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [Élément TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Configuration, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément est la racine de la hiérarchie de schéma d'entrée de l'Assistant Paramétrage du moteur de base de données. Les entrées de l'Assistant Paramétrage du moteur de base de données peuvent être des arguments qui spécifient les bases de données à paramétrer, des charges de travail, des options de paramétrage ou une configuration spécifiée par l'utilisateur.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de l’élément **DTAInput**, consultez [Exemple de fichier d’entrée XML simple &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
