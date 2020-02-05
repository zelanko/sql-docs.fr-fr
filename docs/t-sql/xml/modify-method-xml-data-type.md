---
title: Méthode modify() (type de données xml) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5c98ef9c726d2db5b5ec06d71a00de08288098a0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68051281"
---
# <a name="modify-method-xml-data-type"></a>Méthode modify() (type de données xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifie le contenu d'un document XML. Utilisez cette méthode pour modifier le contenu d’une variable ou colonne de type **xml**. Cette méthode utilise une instruction XML DML pour insérer, mettre à jour ou supprimer les nœuds des données xml. La méthode **modify()** du type de données **xml** ne peut être utilisée que dans la clause SET d’une instruction UPDATE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>Arguments  
 XML_DML  
 Chaîne exprimée en langage XML DML (Data Manipulation Language). Le document XML est mis à jour en fonction de cette expression.  
  
> [!NOTE]  
>  Une erreur est retournée si la méthode **modify()** est appelée en cas de valeur NULL ou a pour résultat une valeur NULL.  
  
## <a name="examples"></a>Exemples  
 Étant donnée que la méthode **modify()** nécessite une chaîne en langage de manipulation de données (DML, Data Manipulation Language) XML, les exemples de méthode **modify()** se trouvent dans les rubriques qui décrivent les instructions DML XML. Pour obtenir ces exemples, consultez [insert &#40;DML XML&#41;](../../t-sql/xml/insert-xml-dml.md), [delete &#40;DML XML&#41;](../../t-sql/xml/delete-xml-dml.md) et [replace value of &#40;DML XML&#41;](../../t-sql/xml/replace-value-of-xml-dml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Langage de manipulation de données XML &#40;DML XML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
