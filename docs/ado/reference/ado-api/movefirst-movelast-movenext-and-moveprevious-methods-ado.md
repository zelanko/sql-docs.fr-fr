---
title: MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MoveLast
- Recordset15::MoveNext
- Recordset15::raw_MoveNext
- Recordset15::raw_MovePrevious
- Recordset15::MoveFirst
- Recordset15::raw_MoveLast
- Recordset15::MovePrevious
- Recordset15::raw_MoveFirst
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- MovePrevious method [ADO]
ms.assetid: a61a01a7-5b33-4150-9126-21dfa63654cb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 905fc532057a827f30735efe067464f488f51dc0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727287"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-ado"></a>MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (ADO)
Déplace vers le premier, au dernier enregistrement suivant ou précédent dans une certaine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet et lui donne de l’enregistre actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez le **MoveFirst** méthode pour déplacer la position actuelle vers le premier enregistrement dans le **Recordset**.  
  
 Utilisez le **MoveLast** méthode pour déplacer la position actuelle vers la dernière enregistrer dans le **Recordset**. Le **Recordset** objet doit prendre en charge les signets ou le déplacement du curseur arrière ; sinon, l’appel de méthode génère une erreur.  
  
 Un appel à **MoveFirst** ou **MoveLast** lorsque le **Recordset** est vide (à la fois **BOF** et **EOF** ont la valeur True) génère une erreur.  
  
 Utilisez le **MoveNext** méthode pour déplacer l’enregistrement actif positionner un enregistrement vers l’avant (vers le bas de la **Recordset**). Si le dernier enregistrement est l’enregistrement actif et que vous appelez le **MoveNext** (méthode), ADO définit l’enregistrement actif à la position après le dernier enregistrement dans le **Recordset** ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) est **True**). Une tentative de déplacement vers l’avant quand le **EOF** propriété est déjà **True** génère une erreur.  
  
 Dans ADO 2.5 et versions ultérieur, lorsque le **Recordset** a été filtrée ou triée et les données de l’enregistrement actif sont modifiées, en appelant le **MoveNext** méthode déplace les enregistrements de curseur deux avant de l’enregistrement actif . Il s’agit, car lorsque l’enregistrement actif est modifié, l’enregistrement suivant devient le nouvel enregistrement en cours. Appel **MoveNext** après la modification déplace le curseur d’un enregistrement du nouvel enregistrement en cours. Cela est différent du comportement dans ADO 2.1 et versions antérieures. Dans les versions antérieures, la modification des données d’un enregistrement en cours dans triée ou filtrée **Recordset** ne modifie pas la position de l’enregistrement en cours, et **MoveNext** déplace le curseur à l’enregistrement suivant immédiatement après l’enregistrement actif.  
  
 Utilisez le **MovePrevious** méthode pour déplacer l’enregistrement actif position d’un enregistrement (vers le haut de la **Recordset**). Le **Recordset** objet doit prendre en charge les signets ou le déplacement du curseur arrière ; sinon, l’appel de méthode génère une erreur. Si le premier enregistrement est l’enregistrement actif et que vous appelez le **MovePrevious** (méthode), ADO définit l’enregistrement actif à la position avant le premier enregistrement dans le **Recordset** ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)est **True**). Une tentative de déplacement vers l’arrière quand le **BOF** propriété est déjà **True** génère une erreur. Si le **Recordset** objet ne prend pas en charge les signets ou le déplacement du curseur arrière, la **MovePrevious** méthode génère une erreur.  
  
 Si le **Recordset** est avant uniquement et que vous souhaitez prendre en charge le défilement arrière et avant, vous pouvez utiliser la [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) propriété pour créer un cache de l’enregistrement qui prendra en charge le déplacement du curseur vers l’arrière via le [déplacer](../../../ado/reference/ado-api/move-method-ado.md) (méthode). Étant donné que les enregistrements mis en cache sont chargées en mémoire, vous devez éviter la mise en cache des enregistrements plus que nécessaire. Vous pouvez appeler le **MoveFirst** méthode en avance seule **Recordset** objet ; cela peut provoquer le fournisseur de réexécuter la commande qui a généré le **Recordset** objet .  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes-exemple (VB)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vb.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes-exemple (VBScript)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes-exemple (VC ++)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vc.md)   
 [Move, méthode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [MoveRecord, méthode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
