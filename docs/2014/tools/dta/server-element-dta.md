---
title: Server, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6c73db809e81cc9b6d1ee182227078a83688384
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52767601"
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
|**Occurrence**|Obligatoire une fois par élément `DTAInput`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Éléments enfants**|[Name, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](name-element-for-server-dta.md)<br /><br /> [Database, élément pour les serveurs &#40;Assistant Paramétrage de base de données&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier qu’un seul `Server` élément pour le `DTAInput` élément. Cet élément porte le nom de **ServerDetailsTypecomplexType** dans le schéma XML de l’Assistant Paramétrage de base de données. Ne confondez pas cet élément `Server` avec l'élément enfant de l'élément `Configuration`. Pour plus d’informations, consultez [Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;](server-element-for-configuration-dta.md).  
  
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
  
  
