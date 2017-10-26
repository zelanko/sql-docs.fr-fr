---
title: OPENQUERY (DMX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENQUERY
dev_langs:
- DMX
helpviewer_keywords:
- OPENQUERY statement
ms.assetid: fe57f3a3-a8e6-402c-995e-bd2fe28a7a7c
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: edfae84521fae05a34448cf0f8ea3ace01e31ed4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---openquery"></a>&lt;requête de source de données&gt; -OPENQUERY
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Remplace la requête de données source par une requête vers une source de données existante. Les instructions INSERT, SELECT FROM PREDICTION JOIN et SELECT FROM NATURAL PREDICTION JOIN prennent en charge **OPENQUERY**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Arguments  
 *source de données nommée*  
 Une source de données qui existe sur le [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données.  
  
 *syntaxe de requête*  
 Syntaxe de requête qui retourne un ensemble de lignes.  
  
## <a name="remarks"></a>Notes  
 **OPENQUERY** fournit un moyen plus sûr pour accéder aux données externes en prenant en charge les autorisations de source de données. La chaîne de connexion étant stockée dans la source de données, les administrateurs peuvent utiliser les propriétés de cette dernière pour gérer l'accès aux données. Pour plus d’informations sur les sources de données, consultez [pris en charge les Sources de données &#40; SSAS - multidimensionnel &#41; ](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Vous pouvez obtenir une liste des sources de données qui sont disponibles sur un serveur en interrogeant le **MDSCHEMA_INPUT_DATASOURCES** de lignes du schéma. Pour plus d’informations sur l’utilisation de **MDSCHEMA_INPUT_DATASOURCES**, consultez [de lignes MDSCHEMA_INPUT_DATASOURCES](../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md).  
  
 Vous pouvez également retourner une liste de sources de données dans la base de données Analysis Services actuelle à l'aide de la requête DMX suivante :  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la source de données MyDS déjà définie dans le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données pour créer une connexion à la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] base de données et de requête le **vTargetMail** vue.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#60; requête de source de données &#62;](../dmx/source-data-query.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

