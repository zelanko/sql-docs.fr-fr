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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e8ac03231680ecd807234b20ac7b210bc480f2c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708485"
---
# <a name="append-method-adox-columns"></a>Append, méthode (colonnes ADOX)
Ajoute un nouveau [colonne](../../../ado/reference/adox-api/column-object-adox.md) de l’objet à la [colonnes](../../../ado/reference/adox-api/columns-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Colonne*  
 Le **colonne** objet à ajouter ou le nom de la colonne à créer et à ajouter.  
  
 *Type*  
 Facultatif. Un **Long** valeur qui spécifie le type de données de la colonne. Le *Type* paramètre correspond à la [Type](../../../ado/reference/adox-api/type-property-column-adox.md) propriété d’un **colonne** objet.  
  
 *DefinedSize*  
 Facultatif. Un **Long** valeur qui spécifie la taille de la colonne. Le *DefinedSize* paramètre correspond à la [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) propriété d’un **colonne** objet.  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout un **colonne** à la **colonnes** collection d’un [Index](../../../ado/reference/adox-api/index-object-adox.md) si le **colonne** n’existe pas dans un [Table](../../../ado/reference/adox-api/table-object-adox.md) déjà ajouté à la [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes ajouter des méthodes, exemple de nom de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append, méthode, Type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, propriété-Exemple (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append, méthode (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append, méthode (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
