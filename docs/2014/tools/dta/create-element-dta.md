---
title: Créer l’élément (DTA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
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
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ce464bc186e4e99d14cf17d0bc442abee0fed39a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141233"
---
# <a name="create-element-dta"></a>Create, élément (Assistant Paramétrage de base de données)
  Contient des informations sur les index, les statistiques ou les structures de segments d'une configuration spécifiée par l'utilisateur.  
  
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
|**Élément parent**|[Recommendation, élément &#40;DTA&#41;](recommendation-element-dta.md)|  
|**Éléments enfants**|[Élément d’index &#40;DTA&#41;](index-element-dta.md)<br /><br /> `Statistics` Élément (consultez [base de données Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) pour plus d’informations)<br /><br /> `Heap` Élément (consultez [base de données Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) pour plus d’informations)|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **CreateTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Il est utilisé pour créer des index, des statistiques ou des structures de segments pour une configuration spécifiée par l'utilisateur. Ne confondez pas cet élément `Create` avec les autres types d'éléments qui peuvent être utilisés pour créer des vues (`CreateViewType`) ou des partitions (`CreatePType`). Reportez-vous à la [de base de données Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) pour plus d’informations sur ces autres `Create` types d’élément.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  