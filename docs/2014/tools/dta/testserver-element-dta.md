---
title: TESTSERVER, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73f5cdd35404617be9563c33574b09f825a2c7ad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63138701"
---
# <a name="testserver-element-dta"></a>TestServer, élément (Assistant Paramétrage de base de données)
  Spécifie le serveur de test à utiliser lors du paramétrage d'un serveur de production.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, longueur illimitée.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Peut être utilisé une seule fois pour chaque élément `TuningOptions`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Réduire la charge de paramétrage du serveur de production](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
