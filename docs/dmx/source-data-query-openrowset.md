---
title: OPENROWSET (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8be3fe8cbf30121ec2895f59306c925a422d5c39
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938124"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;requête&gt; de données sources-OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Remplace la requête de données source par une requête vers un fournisseur externe. Les instructions INSERT, SELECT FROM PREDICTION JOIN et SELECT FROM NATURAL PREDICTION JOIN prennent en charge **OpenRowset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>Arguments  
 *provider_name*  
 Nom d'un fournisseur OLE DB  
  
 *provider_string*  
 Chaîne de connexion OLE DB pour le fournisseur spécifié.  
  
 *query_syntax*  
 Syntaxe de requête qui retourne un ensemble de lignes.  
  
## <a name="remarks"></a>Notes  
 Le fournisseur d’exploration de données établit une connexion à l’objet de source de données à l’aide de *provider_name* et *provider_string* et exécute la requête spécifiée dans *query_syntax* pour récupérer l’ensemble de lignes à partir des données sources.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant peut être utilisé au sein d'une instruction PREDICTION JOIN pour récupérer des données provenant de la base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] à l'aide d'une instruction [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT.  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#60;&#62;de requête de données source](../dmx/source-data-query.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
