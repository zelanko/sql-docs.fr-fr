---
title: Élément de schéma pour la base de données (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f36d625afa75e1bab4108e4a6cb9cadb60eedbf7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47661437"
---
# <a name="schema-element-for-database-dta"></a>Schema, élément pour les bases de données (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Spécifie le schéma de la base de données que vous souhaitez paramétrer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois pour l'élément **Database** spécifié sous l'élément **Server** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Database, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**Éléments enfants**|[Name, élément pour les schémas &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Table, élément pour les schémas &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a> Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Server, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
