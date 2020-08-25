---
description: Append, méthode (colonnes ADOX)
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
ms.openlocfilehash: d17c6823acc945f50e5d8d0543448c997dadc5fe
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771518"
---
# <a name="append-method-adox-columns"></a>Append, méthode (colonnes ADOX)
Ajoute un nouvel objet [Column](./column-object-adox.md) à la collection [Columns](./columns-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Colonne*  
 Objet de **colonne** à ajouter ou nom de la colonne à créer et à ajouter.  
  
 *Type*  
 facultatif. Valeur de type **long** qui spécifie le type de données de la colonne. Le paramètre de *type* correspond à la propriété de [type](./type-property-column-adox.md) d’un objet de **colonne** .  
  
 *DefinedSize*  
 facultatif. Valeur de **type long** qui spécifie la taille de la colonne. Le paramètre *DefinedSize* correspond à la propriété [DefinedSize](./definedsize-property-adox.md) d’un objet **Column** .  
  
> [!NOTE]
>  Une erreur se produit lors de l’ajout d’une **colonne** à la collection **Columns** d’un [index](./index-object-adox.md) si la **colonne** n’existe pas dans une [table](./table-object-adox.md) qui est déjà ajoutée à la collection [tables](./tables-collection-adox.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Columns, collection (ADOX)](./columns-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Columns et tables Append, méthodes, Name, exemple de propriété (VB)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, exemple de propriété (VB)](./parentcatalog-property-example-vb.md)   
 [Append, méthode (groupes ADOX)](./append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](./append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](./append-method-adox-keys.md)   
 [Append, méthode (procédures ADOX)](./append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](./append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](./append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](./append-method-adox-views.md)