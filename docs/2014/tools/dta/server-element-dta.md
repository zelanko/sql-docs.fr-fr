---
title: Élément de serveur (DTA) | Documents Microsoft
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
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 16bfbc4b45f8438ab5a4ab31cdce8183cb473e64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153165"
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
|**Occurrence**|Obligatoire une fois par `DTAInput` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Éléments enfants**|[Nom d’élément pour le serveur &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Élément de base de données pour le serveur &#40;DTA&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier qu’un seul `Server` , élément pour les `DTAInput` élément. Cet élément porte le nom de **ServerDetailsTypecomplexType** dans le schéma XML de l’Assistant Paramétrage de base de données. Ne confondez pas cet `Server` élément avec celui qui est l’enfant de la `Configuration` élément. Pour plus d’informations, consultez [Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](server-element-for-configuration-dta.md).  
  
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
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  