---
title: "ParentCatalog, propriété (ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f5229c37299494ca2b3b31e3ca3e0d091c93d96a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="parentcatalog-property-adox"></a>ParentCatalog, propriété (ADOX)
Spécifie le catalogue parent d’un objet Table, un utilisateur ou colonne pour accéder aux propriétés spécifiques au fournisseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et renvoie un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) objet. Paramètre **ParentCatalog** à open **catalogue** permet d’accéder aux propriétés spécifiques au fournisseur avant d’ajouter une table ou une colonne à un **catalogue** collection.  
  
## <a name="remarks"></a>Notes  
 Certains fournisseurs de données autorise les valeurs de propriété spécifique au fournisseur doivent être écrites uniquement lors de la création : autrement dit, lorsqu’une table ou une colonne est ajouté à son **catalogue** collection. Pour accéder à ces propriétés avant d’ajouter ces objets à un **catalogue**, spécifiez la **catalogue** dans les **ParentCatalog** propriété premier.  
  
 Une erreur se produit lorsque la table ou la colonne est ajouté à un autre **catalogue** à la **ParentCatalog**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Objet de colonne (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Objet table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[Objet utilisateur (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)

