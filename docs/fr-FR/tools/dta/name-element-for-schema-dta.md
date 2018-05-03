---
title: Nom d’élément de schéma (DTA) | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fbf3e0b7d5f78464f39b83a2db1b83e58f29ba4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="name-element-for-schema-dta"></a>Name, élément pour les schémas (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Contient le nom du schéma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, entre 1 et 255 caractères.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par élément **Schema** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a> Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
