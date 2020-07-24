---
title: Name, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
author: rothja
ms.author: jroth
ms.openlocfilehash: 24d86b384a1eb2916e488c17c99e4b9b5962dd1a
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942721"
---
# <a name="name-property-adox"></a>Name, propriété (ADOX)
Indique le nom de l’objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** .  
  
## <a name="remarks"></a>Notes  
 Les noms ne doivent pas nécessairement être uniques dans une collection.  
  
 La propriété de **nom** est en lecture/écriture sur les objets de [colonne](../../../ado/reference/adox-api/column-object-adox.md), de [groupe](../../../ado/reference/adox-api/group-object-adox.md), de [clé](../../../ado/reference/adox-api/key-object-adox.md), d' [index](../../../ado/reference/adox-api/index-object-adox.md), de [table](../../../ado/reference/adox-api/table-object-adox.md)et d' [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) . La propriété **Name** est en lecture seule sur les objets [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md), [procédure](../../../ado/reference/adox-api/procedure-object-adox.md)et [vue](../../../ado/reference/adox-api/view-object-adox.md) .  
  
 Pour les objets en lecture/écriture (**colonne**, **Groupe**, **clé**, **index**, **table** et objets **utilisateur** ), la valeur par défaut est une chaîne vide ("").  
  
> [!NOTE]
>  Pour les clés, cette propriété est en lecture seule sur les objets **clés** déjà ajoutés à une collection. Pour les tables, cette propriété est en lecture seule pour les objets de **table** déjà ajoutés à une collection.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
        [Group, objet (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)  
        [Index, objet (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)  
    :::column-end:::
    :::column:::
        [Key, objet (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)  
        [Procedure, objet (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)  
        [Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)  
    :::column-end:::
    :::column:::
        [Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
        [User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
        [View, objet (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [Columns et tables Append, méthodes, Name, exemple de propriété (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog, exemple de propriété (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
