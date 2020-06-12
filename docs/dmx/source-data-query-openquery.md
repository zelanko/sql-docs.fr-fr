---
title: OPENQUERY (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d8e3b85f3d18b25f9dda1ef4f442ec0822257fae
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670034"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;requête de données sources &gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Remplace la requête de données source par une requête vers une source de données existante. Les instructions INSERT, SELECT FROM PREDICTION JOIN et SELECT FROM NATURAL PREDICTION JOIN prennent en charge **OPENQUERY**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Arguments  
 *DataSource nommée*  
 Source de données qui existe sur la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données.  
  
 *syntaxe de la requête*  
 Syntaxe de requête qui retourne un ensemble de lignes.  
  
## <a name="remarks"></a>Notes  
 **OPENQUERY** offre une méthode plus sécurisée pour accéder aux données externes en prenant en charge les autorisations de source de données. La chaîne de connexion étant stockée dans la source de données, les administrateurs peuvent utiliser les propriétés de cette dernière pour gérer l'accès aux données. Pour plus d’informations sur les sources de données, consultez [sources de données prises en charge &#40;SSAS-&#41;multidimensionnel ](https://docs.microsoft.com/analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional).  
  
 Vous pouvez obtenir la liste des sources de données disponibles sur un serveur en interrogeant l’ensemble de lignes de schéma **MDSCHEMA_INPUT_DATASOURCES** . Pour plus d’informations sur l’utilisation de **MDSCHEMA_INPUT_DATASOURCES**, consultez [MDSCHEMA_INPUT_DATASOURCES rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset).  
  
 Vous pouvez également retourner une liste de sources de données dans la base de données Analysis Services actuelle à l'aide de la requête DMX suivante :  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la source de données MyDS déjà définie dans la [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données pour créer une connexion à la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] base de données et interroger la vue **vTargetMail** .  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#60;&#62;de requête de données source](../dmx/source-data-query.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
