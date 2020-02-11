---
title: Append, méthode (clés ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Keys::Append
- Keys::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd66edb75bec4f4b7e35c53c9ebeabd9b3c75d83
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967292"
---
# <a name="append-method-adox-keys"></a>Append, méthode (clés ADOX)
Ajoute un nouvel objet [clé](../../../ado/reference/adox-api/key-object-adox.md) à la collection de [clés](../../../ado/reference/adox-api/keys-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Keys.Append Key [,KeyType] [,Column] [,RelatedTable] [,RelatedColumn]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Clé*  
 Objet **clé** à ajouter ou nom de la clé à créer et à ajouter.  
  
 *KeyType*  
 facultatif. Valeur de type **long** qui spécifie le type de clé. Le paramètre de *clé* correspond à la propriété de [type](../../../ado/reference/adox-api/type-property-key-adox.md) d’un objet **clé** .  
  
 *Colonne*  
 facultatif. Valeur de **chaîne** qui spécifie le nom de la colonne à indexer. Le paramètre *Columns* correspond à la valeur de la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) d’un objet [Column](../../../ado/reference/adox-api/column-object-adox.md) .  
  
 *RelatedTable*  
 facultatif. Valeur de **chaîne** qui spécifie le nom de la table associée. Le paramètre *RelatedTable* correspond à la valeur de la propriété **Name** d’un objet [table](../../../ado/reference/adox-api/table-object-adox.md) .  
  
 *; RelatedColumn*  
 facultatif. Valeur de **chaîne** qui spécifie le nom de la colonne associée pour une clé étrangère. Le paramètre *RelatedColumn* correspond à la valeur de la propriété **Name** d’un objet [Column](../../../ado/reference/adox-api/column-object-adox.md) .  
  
## <a name="remarks"></a>Notes  
 Le paramètre *Columns* peut prendre soit le nom d’une colonne, soit un tableau de noms de colonnes.  
  
## <a name="applies-to"></a>S'applique à  
 [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Append, méthode (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append, méthode (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append, méthode (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
