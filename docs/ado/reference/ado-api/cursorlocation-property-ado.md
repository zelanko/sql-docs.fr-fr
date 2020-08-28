---
description: CursorLocation, propriété (ADO)
title: CursorLocation, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
author: rothja
ms.author: jroth
ms.openlocfilehash: 121aeef137946152a82808c8a439f2e5d03a2c94
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974460"
---
# <a name="cursorlocation-property-ado"></a>CursorLocation, propriété (ADO)
Indique l’emplacement du service de curseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui peut être définie sur l’une des valeurs [CursorLocationEnum](./cursorlocationenum.md) .  
  
## <a name="remarks"></a>Notes  
 Cette propriété vous permet de choisir entre différentes bibliothèques de curseurs accessibles au fournisseur. En règle générale, vous pouvez choisir entre l’utilisation d’une bibliothèque de curseurs côté client ou celle qui est située sur le serveur.  
  
 Ce paramètre de propriété affecte les connexions établies uniquement après la définition de la propriété. La modification de la propriété **CursorLocation** n’a aucun effet sur les connexions existantes.  
  
 Les curseurs retournés par la méthode [Execute](./execute-method-ado-connection.md) héritent de ce paramètre. Les objets **Recordset** héritent automatiquement de ce paramètre de leurs connexions associées.  
  
 Cette propriété est en lecture/écriture sur une [connexion](./connection-object-ado.md) ou un [Recordset](./recordset-object-ado.md)fermé, et en lecture seule sur un **Recordset**ouvert.  
  
> [!NOTE]
>  **Utilisation des services de données distants** Lorsqu’elle est utilisée sur un objet **Recordset** ou **Connection** côté client, la propriété **CursorLocation** ne peut avoir que la valeur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Connection, objet (ADO)](./connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset, objet (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [Annexe A : Fournisseurs](../../guide/appendixes/appendix-a-providers.md)