---
description: Type, propriété (colonne) (ADOX)
title: Type, propriété (Column) (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::Type
- _Column::GetType
- _Column::get_Type
- _Column::put_Type
- _Column::PutType
helpviewer_keywords:
- Type property [ADOX]
ms.assetid: 5c6718b6-f728-478a-8afb-5d17b0a91d1f
author: rothja
ms.author: jroth
ms.openlocfilehash: 70d8700f953a87fa3326f6a1c0985be1f6ca3dac
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769218"
---
# <a name="type-property-column-adox"></a>Type, propriété (colonne) (ADOX)
Indique le type de données d’une colonne.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui peut être l’une des constantes [DataTypeEnum](../ado-api/datatypeenum.md) . La valeur par défaut est **adVarWChar**.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est en lecture/écriture jusqu’à ce que l’objet de [colonne](./column-object-adox.md) soit ajouté à une collection ou à un autre objet, après quoi il est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
 [Column, objet (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ParentCatalog, exemple de propriété (VB)](./parentcatalog-property-example-vb.md)   
 [Type, propriété (Key) (ADOX)](./type-property-key-adox.md)   
 [Type, propriété (table) (ADOX)](./type-property-table-adox.md)