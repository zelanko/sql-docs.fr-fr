---
title: Nom d’élément de serveur (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 750911c19224ff088fee5c27272bf13c14875975
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62657263"
---
# <a name="name-element-for-server-dta"></a>Name, élément pour les serveurs (Assistant Paramétrage de base de données)
  Contient le nom du serveur sur lequel résident les bases de données que vous souhaitez paramétrer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`string`, entre 1 et 255 caractères.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par élément **Server** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Server, élément &#40;Assistant Paramétrage de base de données&#41;](server-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour voir un exemple d’utilisation de l’élément **Name** , consultez [Server Element &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
