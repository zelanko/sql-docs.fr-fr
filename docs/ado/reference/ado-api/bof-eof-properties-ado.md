---
title: BOF, EOF, propriétés (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::BOF
- Recordset15::EOF
helpviewer_keywords:
- EOF property [ADO]
- BOF property [ADO]
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9a449c0e635c7fe0e63bc1f4d8b1b0b91712135d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696291"
---
# <a name="bof-eof-properties-ado"></a>BOF, EOF, propriétés (ADO)
-   **BOF** indique que la position actuelle est avant le premier enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
-   **EOF** indique que la position actuelle se trouve après le dernier enregistrement dans un **Recordset** objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Le **BOF** et **EOF** propriétés retour **booléenne** valeurs.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **BOF** et **EOF** propriétés pour déterminer si un **Recordset** objet contient des enregistrements ou si vous avez dépassé les limites d’un **Recordset**  de l’objet lorsque vous déplacez d’un enregistrement à l’autre.  
  
 Le **BOF** retourne de la propriété **True** (-1) si la position actuelle est avant le premier enregistrement et **False** (0) si la position actuelle est sur ou après le premier enregistrement.  
  
 Le **EOF** retourne de la propriété **True** si la position actuelle est après le dernier enregistrement et **False** si la position actuelle est l’ou avant le dernier enregistrement.  
  
 Si le **BOF** ou **EOF** propriété est **True**, il n’existe aucun enregistrement actif.  
  
 Si vous ouvrez un **Recordset** objet ne contenant aucun enregistrement, la **BOF** et **EOF** propriétés sont définies sur **True** (voir la [ RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) propriété pour plus d’informations sur cet état d’un **Recordset**). Lorsque vous ouvrez un **Recordset** objet qui contient au moins un enregistrement, le premier enregistrement est l’enregistrement actif et le **BOF** et **EOF** propriétés sont **False** .  
  
 Si vous supprimez le dernier enregistrement restant dans le **Recordset** objet, le **BOF** et **EOF** propriétés peuvent rester **False** jusqu'à ce que vous tentative d’enregistrement.  
  
 Ce tableau montre qui **déplacer** les méthodes sont autorisées avec les différentes combinaisons de le **BOF** et **EOF** propriétés.  
  
||MoveFirst,<br /><br /> MoveLast|MovePrevious,<br /><br /> Déplacer < 0|Déplacer le 0|MoveNext,<br /><br /> Déplacer > 0|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF**=**True**, **EOF**=**False**|Autorisé|Error|Error|Autorisé|  
|**BOF**=**False**, **EOF**=**True**|Autorisé|Autorisé|Error|Error|  
|Les deux **True**|Error|Error|Error|Error|  
|Les deux **False**|Autorisé|Autorisé|Autorisé|Autorisé|  
  
 Ce qui permet un **déplacer** méthode ne garantit pas que la méthode parviendra à localiser un enregistrement ; cela signifie simplement que l’appel spécifié **déplacer** méthode ne générera pas d’une erreur.  
  
 Le tableau suivant montre ce qui se passe à la **BOF** et **EOF** les paramètres de propriété lorsque vous appelez différentes **déplacer** méthodes, mais ne parvenez pas à trouver un enregistrement.  
  
||BOF|EOF|  
|------|---------|---------|  
|**MoveFirst**, **MoveLast**|La valeur **True**|La valeur **True**|  
|**Move** 0|Aucune modification|Aucune modification|  
|**MovePrevious**, **déplacer** < 0|La valeur **True**|Aucune modification|  
|**MoveNext**, **déplacer** > 0|Aucune modification|La valeur **True**|  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BOF, EOF et Bookmark, exemple de propriétés (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF, EOF et Bookmark, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
