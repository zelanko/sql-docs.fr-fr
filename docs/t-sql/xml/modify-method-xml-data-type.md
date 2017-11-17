---
title: "Modify(), méthode (Type de données xml) | Documents Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81838bf62f9b2c92dce4df8a167785fdfbf7abb2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="modify-method-xml-data-type"></a>Méthode modify() (type de données xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifie le contenu d'un document XML. Utilisez cette méthode pour modifier le contenu d’un **xml** variable de type ou de la colonne. Cette méthode utilise une instruction XML DML pour insérer, mettre à jour ou supprimer les nœuds des données xml. Le **modify()** méthode de la **xml** type de données peut uniquement être utilisé dans la clause SET d’une instruction UPDATE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Arguments  
 XML_DML  
 Chaîne exprimée en langage XML DML (Data Manipulation Language). Le document XML est mis à jour en fonction de cette expression.  
  
> [!NOTE]  
>  Une erreur est retournée si le **modify()** méthode est appelée sur une valeur null ou aboutit à une valeur null.  
  
## <a name="examples"></a>Exemples  
 Étant donné que la **modify()** méthode requiert une chaîne dans le XML langage DML (Data Manipulation), les exemples de **modify()** sont contenues dans les rubriques qui décrivent les instructions XML DML. Pour ces exemples, consultez [insert &#40; XML DML &#41; ](../../t-sql/xml/insert-xml-dml.md), [Supprimer &#40; XML DML &#41; ](../../t-sql/xml/delete-xml-dml.md) et [remplacer la valeur de &#40; XML DML &#41; ](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [XML Data Modification Language &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

