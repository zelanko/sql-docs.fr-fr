---
title: AbsolutePosition, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePosition
helpviewer_keywords:
- AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4444c54df6e3629e7f69e3fe0d54625f66c3e703
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813157"
---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition, propriété (ADO)
Indique la position ordinale d’une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) enregistrement en cours de l’objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Pour le code 32 bits, définit ou retourne un **Long** valeur entre 1 et le nombre d’enregistrements dans le **Recordset** objet ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)), ou retourne une de la [ PositionEnum](../../../ado/reference/ado-api/positionenum.md) valeurs.  
  
 Pour le code de 64 bits, utilisez un type de données qui fournit pour le stockage d’une valeur 64 bits. Par exemple, vous pouvez utiliser Long ou une autre valeur qui est de longueur de 64 bits comme DBORDINAL. N’utilisez pas **PositionEnum** valeurs dans la mesure où ils sont limités à la longueur de 32 bits.  
  
## <a name="remarks"></a>Notes  
 Pour définir le **AbsolutePosition** propriété, ADO exige que le fournisseur OLE DB que vous utilisez implémente le [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx) interface.  
  
 L’accès à la **AbsolutePosition** propriété d’un **Recordset** qui a été ouvert avec l’avant uniquement ou curseur dynamique génère l’erreur **adErrFeatureNotAvailable**. Avec d’autres types de curseur, la position correcte sera retournée tant que le fournisseur OLE DB prend en charge la **IRowsetScroll:IRowsetLocate** interface. Si le fournisseur ne prend pas en charge la **IRowsetScroll** interface, la propriété est définie sur **adPosUnknown**. Consultez la documentation de votre fournisseur déterminer si elle prend en charge **IRowsetScroll**.  
  
 Utilisez le **AbsolutePosition** propriété pour accéder à un enregistrement en fonction de sa position ordinale dans la **Recordset** objet, ou pour déterminer la position ordinale de l’enregistrement actif. Le fournisseur doit prendre en charge les fonctionnalités requises pour cette propriété doit être disponible.  
  
 Comme le [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) propriété, **AbsolutePosition** basé sur 1 et est égale à 1 lors de l’enregistrement actif est le premier enregistrement dans le **Recordset**. Vous pouvez obtenir le nombre total d’enregistrements dans le **Recordset** de l’objet à partir de la [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) propriété.  
  
 Lorsque vous définissez la **AbsolutePosition** propriété, même si elle est à un enregistrement dans le cache actuel, ADO recharge le cache avec un nouveau groupe d’enregistrements en commençant par l’enregistrement que vous avez spécifié. Le [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) propriété détermine la taille de ce groupe.  
  
> [!NOTE]
>  Vous ne devez pas utiliser le **AbsolutePosition** propriété en tant que numéro d’enregistrement de substitution. La position d’un enregistrement donné change lorsque vous supprimez un enregistrement précédent. Il n’existe également aucune assurance qu’un enregistrement donné auront le même **AbsolutePosition** si le **Recordset** objet est actualisé ou rouvert. Les signets sont toujours la méthode recommandée de conserver et revenir à une position donnée et sont la seule façon de se positionner dans tous les types de **Recordset** objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AbsolutePosition et CursorLocation, exemple de propriétés (VB)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [AbsolutePosition et CursorLocation, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [RecordCount, propriété (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
