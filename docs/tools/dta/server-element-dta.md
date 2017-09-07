---
title: "Élément de serveur (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a70751047dec6fb9f5826ce23bf81381cba828cf
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="server-element-dta"></a>Server, élément (Assistant Paramétrage de base de données)
  Contient les informations d'identification du serveur sur lequel résident les bases de données que vous souhaitez paramétrer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par élément **DTAInput** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40; DTA &#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les serveurs &#40; DTA &#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Élément de base de données de serveur &#40; DTA &#41;](../../tools/dta/database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez spécifier qu’un seul élément **Server** pour l’élément **DTAInput** . Cet élément porte le nom de **ServerDetailsTypecomplexType** dans le schéma XML de l’Assistant Paramétrage de base de données. Ne confondez pas cet élément **Server** avec l’élément enfant de l’élément **Configuration**. Pour plus d’informations, consultez [Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/server-element-for-configuration-dta.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier la table **Sales.SalesPerson** dans la base de données **AdventureWorks** située sur SERVER001 :  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
