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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965584"
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog, propriété (ADOX)
Spécifie le catalogue parent d’un objet table, User ou Column pour permettre l’accès aux propriétés spécifiques au fournisseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et retourne un objet [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md) . Définir **ParentCatalog** sur un **catalogue** ouvert permet d’accéder aux propriétés spécifiques au fournisseur avant d’ajouter une table ou une colonne à une collection de **catalogues** .  
  
## <a name="remarks"></a>Notes  
 Certains fournisseurs de données autorisent l’écriture de valeurs de propriétés spécifiques au fournisseur uniquement lors de la création : autrement dit, lorsqu’une table ou une colonne est ajoutée à sa collection de **catalogues** . Pour accéder à ces propriétés avant d’ajouter ces objets à un **catalogue**, spécifiez d’abord le **catalogue** dans la propriété **ParentCatalog** .  
  
 Une erreur se produit lorsque la table ou la colonne est ajoutée à un autre **catalogue** que le **ParentCatalog**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
