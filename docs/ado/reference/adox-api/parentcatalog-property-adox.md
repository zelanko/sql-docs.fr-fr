---
description: ParentCatalog, propriété (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4087e3bf0ab7b9e65d616907b1f5db3c87a0f75e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769938"
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog, propriété (ADOX)
Spécifie le catalogue parent d’un objet table, User ou Column pour permettre l’accès aux propriétés spécifiques au fournisseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et retourne un objet [catalogue](./catalog-object-adox.md) . Définir **ParentCatalog** sur un **catalogue** ouvert permet d’accéder aux propriétés spécifiques au fournisseur avant d’ajouter une table ou une colonne à une collection de **catalogues** .  
  
## <a name="remarks"></a>Notes  
 Certains fournisseurs de données autorisent l’écriture de valeurs de propriétés spécifiques au fournisseur uniquement lors de la création : autrement dit, lorsqu’une table ou une colonne est ajoutée à sa collection de **catalogues** . Pour accéder à ces propriétés avant d’ajouter ces objets à un **catalogue**, spécifiez d’abord le **catalogue** dans la propriété **ParentCatalog** .  
  
 Une erreur se produit lorsque la table ou la colonne est ajoutée à un autre **catalogue** que le **ParentCatalog**.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Column, objet (ADOX)](./column-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table, objet (ADOX)](./table-object-adox.md)  
    :::column-end:::
    :::column:::
        [User, objet (ADOX)](./user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [ParentCatalog, exemple de propriété (VB)](./parentcatalog-property-example-vb.md)