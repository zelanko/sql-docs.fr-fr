---
title: Append, méthode (colonnes ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e69f2510e825a935cf7eb34951051c1e3848bb9
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764040"
---
# <a name="append-method-adox-columns"></a>Append, méthode (colonnes ADOX)
Ajoute un nouvel objet [Column](../../../ado/reference/adox-api/column-object-adox.md) à la collection [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Colonne*  
 Objet de **colonne** à ajouter ou nom de la colonne à créer et à ajouter.  
  
 *Type*  
 facultatif. Valeur de type **long** qui spécifie le type de données de la colonne. Le paramètre de *type* correspond à la propriété de [type](../../../ado/reference/adox-api/type-property-column-adox.md) d’un objet de **colonne** .  
  
 *DefinedSize*  
 facultatif. Valeur de **type long** qui spécifie la taille de la colonne. Le paramètre *DefinedSize* correspond à la propriété [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) d’un objet **Column** .  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout d’une **colonne** à la collection **Columns** d’un [index](../../../ado/reference/adox-api/index-object-adox.md) si la **colonne** n’existe pas dans une [table](../../../ado/reference/adox-api/table-object-adox.md) qui est déjà ajoutée à la collection [tables](../../../ado/reference/adox-api/tables-collection-adox.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Columns et tables Append, méthodes, Name, exemple de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append, méthode (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append, méthode (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
