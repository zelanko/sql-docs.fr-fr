---
title: "Append (méthode) (groupes ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Groups::raw_Append
- Groups::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 56b94fc6-7ef0-4e4a-82a3-033b94c46036
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 232f7d51b00d9c22689f126518bbaddacc9a3b8f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="append-method-adox-groups"></a>Append (méthode) (groupes ADOX)
Ajoute un nouveau [groupe](../../../ado/reference/adox-api/group-object-adox.md) de l’objet à la [groupes](../../../ado/reference/adox-api/groups-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Grouper*  
 Le **groupe** objet à ajouter ou le nom du groupe à créer et à ajouter.  
  
## <a name="remarks"></a>Notes  
 Le **groupes** collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) représente tous les comptes de groupe du catalogue. Le **groupes** collection pour un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) représente uniquement le groupe auquel appartient l’utilisateur.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création de groupes.  
  
> [!NOTE]
>  Avant d’ajouter un **groupe** de l’objet à la **groupes** collection d’un **utilisateur** objet, un **groupe** objet avec le même [nom](../../../ado/reference/adox-api/name-property-adox.md) que celui à ajouter doit déjà exister dans le **groupes** collection de la **catalogue**.  
  
## <a name="applies-to"></a>S'applique à  
 [Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisateurs et groupes Append, ChangePassword, méthodes-exemple (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append (méthode) (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (méthode) (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (méthode) (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (méthode) (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (méthode) (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (méthode) (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
