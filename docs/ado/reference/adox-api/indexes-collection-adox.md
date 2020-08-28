---
description: Indexes, collection (ADOX)
title: Indexes, collection (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Indexes
- Indexes
helpviewer_keywords:
- Indexes collection [ADOX]
ms.assetid: 184cf536-455c-42be-bf1c-a5c25bade961
author: rothja
ms.author: jroth
ms.openlocfilehash: daea070c8bd39d6208404f119578773382078634
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984190"
---
# <a name="indexes-collection-adox"></a>Indexes, collection (ADOX)
Contient tous les objets [index](./index-object-adox.md) d’une table.  
  
## <a name="remarks"></a>Notes  
 La méthode [Append](./append-method-adox-indexes.md) d’une collection **indexes** est unique pour ADOX. Vous pouvez :  
  
-   Ajoutez un nouvel index à la collection à l’aide de la méthode **Append** .  
  
 Les propriétés et les méthodes restantes sont standard pour les collections ADO. Vous pouvez :  
  
-   Accédez à un index dans la collection à l’aide de la propriété [Item](../ado-api/item-property-ado.md) .  
  
-   Retourne le nombre d’index contenus dans la collection avec la propriété [Count](../ado-api/count-property-ado.md) .  
  
-   Supprimez un index de la collection à l’aide de la méthode [Delete](./delete-method-adox-collections.md) .  
  
-   Mettez à jour les objets de la collection pour refléter le schéma de base de données actuel avec la méthode [Refresh](../ado-api/refresh-method-ado.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de la collection Indexes](./indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Indexes, exemple de méthode Append (VB)](./indexes-append-method-example-vb.md)   
 [Index, objet (ADOX)](./index-object-adox.md)