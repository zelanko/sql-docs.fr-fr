---
title: "CursorLocation, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6679a7a8a83f954039587776e5e668bd5ed05365
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cursorlocation-property-ado"></a>CursorLocation, propriété (ADO)
Indique l’emplacement du service de curseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur peut être définie à une de la [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) valeurs.  
  
## <a name="remarks"></a>Notes  
 Cette propriété vous permet de choisir entre les différentes bibliothèques de curseurs accessibles au fournisseur. En règle générale, vous pouvez choisir entre l’utilisation d’une bibliothèque de curseurs côté client ou qui se trouve sur le serveur.  
  
 Ce paramètre de propriété affecte les connexions établies après que la propriété a été définie. Modification de la **CursorLocation** propriété n’a aucun effet sur les connexions existantes.  
  
 Les curseurs renvoyés par la [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) méthode héritent de ce paramètre. **Jeu d’enregistrements** objets héritent automatiquement ce paramètre de leurs connexions associées.  
  
 Cette propriété est en lecture/écriture sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ou un fermé [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)et en lecture seule sur open **Recordset**.  
  
> [!NOTE]
>  **Utilisation du Service de données à distance** lorsqu’il est utilisé sur un côté client **Recordset** ou **connexion** objet, le **CursorLocation** propriété peut uniquement être définie sur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
