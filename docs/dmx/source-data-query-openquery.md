---
title: OPENQUERY (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1079fbb02026e2043767082d5def7fac37322ef2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077732"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;requête de source de données&gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 **OPENQUERY** fournit un moyen plus sûr pour accéder aux données externes en prenant en charge les autorisations de source de données. La chaîne de connexion étant stockée dans la source de données, les administrateurs peuvent utiliser les propriétés de cette dernière pour gérer l'accès aux données. Pour plus d’informations sur les sources de données, consultez [pris en charge les Sources de données &#40;SSAS - multidimensionnel&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Vous pouvez obtenir une liste des sources de données qui sont disponibles sur un serveur en interrogeant le **MDSCHEMA_INPUT_DATASOURCES** ensemble de lignes de schéma. Pour plus d’informations sur l’utilisation de **MDSCHEMA_INPUT_DATASOURCES**, consultez [de lignes MDSCHEMA_INPUT_DATASOURCES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset).  
  
 Vous pouvez également retourner une liste de sources de données dans la base de données Analysis Services actuelle à l'aide de la requête DMX suivante :  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la source de données MyDS déjà définie dans le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données pour créer une connexion à la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] base de données et de requête le **vTargetMail** vue.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#60;requête de source de données&#62;](../dmx/source-data-query.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
