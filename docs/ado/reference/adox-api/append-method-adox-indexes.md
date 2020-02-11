---
title: Append, méthode (Index ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Indexes::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6695769f-275b-4b70-81bd-1a5f7d74926c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef30faf0fef05c4e86ffb4d2c21781592094c198
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967300"
---
# <a name="append-method-adox-indexes"></a>Append, méthode (index ADOX)
Ajoute un nouvel objet [index](../../../ado/reference/adox-api/index-object-adox.md) à la collection d' [index](../../../ado/reference/adox-api/indexes-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Indexes.Append Index [,Columns]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Évaluer*  
 Objet d' **index** à ajouter ou nom de l’index à créer et à ajouter.  
  
 *Colonnes*  
 facultatif. Valeur de **type Variant** qui spécifie le ou les noms de la ou des colonnes à indexer. Le paramètre *Columns* correspond à la ou aux valeurs de la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) d’un ou plusieurs objets [Column](../../../ado/reference/adox-api/column-object-adox.md) .  
  
## <a name="remarks"></a>Notes  
 Le paramètre *Columns* peut prendre soit le nom d’une colonne, soit un tableau de noms de colonnes.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création d’index.  
  
## <a name="applies-to"></a>S'applique à  
 [Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Indexes, exemple de méthode Append (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Append, méthode (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append, méthode (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append, méthode (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append, méthode (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
