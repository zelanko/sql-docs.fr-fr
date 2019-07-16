---
title: ParentCatalog, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8bc9527109aaa4a3a8063b26a594c9bdb978dcf3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965584"
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog, propriété (ADOX)
Spécifie le catalogue parent d’un objet Table, un utilisateur ou colonne pour fournir l’accès aux propriétés spécifiques au fournisseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et renvoie un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) objet. Paramètre **ParentCatalog** pour une ouverture **catalogue** permet d’accéder aux propriétés spécifiques au fournisseur avant l’ajout d’une table ou une colonne à un **catalogue** collection.  
  
## <a name="remarks"></a>Notes  
 Certains fournisseurs de données autorisent les valeurs de propriété spécifique au fournisseur à écrire uniquement lors de la création : autrement dit, quand une table ou une colonne est ajouté à son **catalogue** collection. Pour accéder à ces propriétés avant d’ajouter ces objets à un **catalogue**, spécifiez la **catalogue** dans le **ParentCatalog** propriété premier.  
  
 Une erreur se produit lorsque la table ou la colonne est ajouté à un autre **catalogue** que le **ParentCatalog**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
