---
title: Move, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Move
- Recordset15::raw_Move
helpviewer_keywords:
- Move method [ADO]
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8306a7d8e3247e77579d0bebc9147c3f9a1cc56
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789327"
---
# <a name="move-method-ado"></a>Move, méthode (ADO)
Déplace la position de l’enregistrement actif dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>Paramètres  
 *NumRecords*  
 Signé **Long** expression qui spécifie le nombre d’enregistrements qui déplace la position actuelle.  
  
 *Démarrer*  
 Facultatif. Un **chaîne** valeur ou **Variant** qui correspond à un signet. Vous pouvez également utiliser un [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) valeur.  
  
## <a name="remarks"></a>Notes  
 Le **déplacer** méthode est prise en charge sur tous les **Recordset** objets.  
  
 Si le *NbEnregistrements* argument est supérieur à zéro, la position actuelle se déplace vers l’avant (vers la fin de la **Recordset**). Si *NbEnregistrements* est inférieur à zéro, la position actuelle se déplace vers l’arrière (vers le début de la **Recordset**).  
  
 Si le **déplacer** appel serait déplace la position actuelle vers un point situé avant le premier enregistrement, ADO définit l’enregistrement actif à la position avant le premier enregistrement dans le jeu d’enregistrements ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) est **True** ). Une tentative de déplacement vers l’arrière quand le **BOF** propriété est déjà **True** génère une erreur.  
  
 Si le **déplacer** appel déplacerait la position actuelle vers un point après le dernier enregistrement, ADO définit l’enregistrement actif à la position après le dernier enregistrement dans le jeu d’enregistrements ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) est **True** ). Une tentative de déplacement vers l’avant quand le **EOF** propriété est déjà **True** génère une erreur.  
  
 Appel de la **déplacer** méthode à partir de vide **Recordset** objet génère une erreur.  
  
 Si vous passez le *Démarrer* argument, le déplacement est relatif à l’enregistrement avec ce signet, en supposant que le **Recordset** objet prend en charge les signets. Si non spécifié, le déplacement est relatif à l’enregistrement actif.  
  
 Si vous utilisez le [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) propriété à mettre en cache localement les enregistrements à partir du fournisseur, en passant un *NbEnregistrements* argument qui déplace la position actuelle en dehors du groupe actuel d’enregistrements mis en cache force ADO à récupérer un nouveau groupe d’enregistrements, à partir de l’enregistrement de destination. Le **CacheSize** propriété détermine la taille du groupe qui vient d’être extrait et l’enregistrement de destination est le premier enregistrement récupéré.  
  
 Si le **Recordset** objet est avant uniquement, un utilisateur peut toujours se transmettre un *NbEnregistrements* argument inférieur à zéro, fournies à la destination se trouve dans le jeu actuel d’enregistrements mis en cache. Si le **déplacer** appel déplacerait la position actuelle à un enregistrement avant le premier enregistrement mis en cache, une erreur se produit. Par conséquent, vous pouvez utiliser un cache d’enregistrements qui prend en charge le défilement complète sur un fournisseur qui prend en charge que le défilement avant. Étant donné que les enregistrements mis en cache sont chargées en mémoire, vous devez éviter la mise en cache des enregistrements plus que nécessaire. Même si uniquement un type avant **Recordset** déplace les prend en charge l’objet vers l’arrière de cette façon, l’appel la [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) méthode sur n’importe quel avant uniquement **Recordset** objet sera toujours génère une erreur.  
  
> [!NOTE]
>  Prise en charge de la progression vers l’arrière en avant uniquement **Recordset** n’est pas prévisible, en fonction de votre fournisseur. Si l’enregistrement en cours a été positionné après le dernier enregistrement dans le **Recordset**, **déplacer** descendante peut ne pas entraîner la bonne position actuelle.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Move, exemple de méthode (VB)](../../../ado/reference/ado-api/move-method-example-vb.md)   
 [Move, exemple de méthode (VBScript)](../../../ado/reference/ado-api/move-method-example-vbscript.md)   
 [Move, exemple de méthode (VC ++)](../../../ado/reference/ado-api/move-method-example-vc.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [MoveRecord, méthode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
