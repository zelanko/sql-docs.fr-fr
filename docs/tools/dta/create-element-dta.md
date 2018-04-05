---
title: Créer l’élément (DTA) | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
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
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee12c846e9f95eea1f5a4b798d2651a92ab8039f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="create-element-dta"></a>Create, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Contient des informations sur les index, statistiques ou structures de segments dans une configuration spécifiée par l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois pour chaque type de structure PDS (index, statistiques ou structures de segments).|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Recommendation, élément &#40; DTA &#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Éléments enfants**|[Index, élément &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/index-element-dta.md)<br /><br /> Élément**Statistics** (pour plus d’informations, consultez [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) (Schéma XML de l’Assistant Paramétrage du moteur de base de données))<br /><br /> Élément**Heap** (pour plus d’informations, consultez [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) (Schéma XML de l’Assistant Paramétrage du moteur de base de données))|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **CreateTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Il est utilisé pour créer des index, des statistiques ou des structures de segments pour une configuration spécifiée par l'utilisateur. Ne confondez pas cet élément **Create** avec les autres types d’éléments qui peuvent être utilisés pour créer des vues (**CreateViewType**) ou des partitions (**CreatePType**). Pour plus d’informations sur les autres types d’éléments [Create](http://schemas.microsoft.com/sqlserver/) , consultez **Database Engine Tuning Advisor XML schema** (Schéma XML de l’Assistant Paramétrage du moteur de base de données).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
