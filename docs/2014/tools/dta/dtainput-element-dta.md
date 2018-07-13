---
title: DTAInput, élément (DTA) | Microsoft Docs
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
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a754e81ea8fe094bb840cb57851685b3b6626521
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179017"
---
# <a name="dtainput-element-dta"></a>DTAInput, élément (Assistant Paramétrage de base de données)
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
|**Élément parent**|[DTAXML, élément &#40;DTA&#41;](dtaxml-element-dta.md)|  
|**Éléments enfants**|[Élément de serveur &#40;DTA&#41;](server-element-dta.md)<br /><br /> [Workload, élément &#40;DTA&#41;](workload-element-dta.md)<br /><br /> [TuningOptions, élément &#40;DTA&#41;](tuningoptions-element-dta.md)<br /><br /> [Élément de configuration &#40;DTA&#41;](configuration-element-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément est la racine de la hiérarchie de schéma d'entrée de l'Assistant Paramétrage du moteur de base de données. Les entrées de l'Assistant Paramétrage du moteur de base de données peuvent être des arguments qui spécifient les bases de données à paramétrer, des charges de travail, des options de paramétrage ou une configuration spécifiée par l'utilisateur.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de l’élément **DTAInput**, consultez [Exemple de fichier d’entrée XML simple &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
