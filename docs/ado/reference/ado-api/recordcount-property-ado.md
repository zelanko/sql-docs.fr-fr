---
title: RecordCount, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa6f29c480244919de71d06cf3d56e672f00c47f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240060"
---
# <a name="recordcount-property-ado"></a>RecordCount, propriété (ADO)

Indique le nombre d’enregistrements dans une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.
  
## <a name="return-value"></a>Valeur de retour

Retourne un **Long** valeur qui indique le nombre d’enregistrements dans le **Recordset**.
  
## <a name="remarks"></a>Notes

Utilisez le **RecordCount** propriété pour déterminer le nombre d’enregistrements sont dans un **Recordset** objet. La propriété retourne -1 quand ADO ne peut pas déterminer le nombre d’enregistrements ou si le type de curseur ou le fournisseur ne prend pas en charge **RecordCount**. Lire le **RecordCount** propriété sur un fermé **Recordset** provoque une erreur.

#### <a name="bookmarks-or-approximate-positioning"></a>Positionnement approximatif ou les signets

Si l’objet Recordset *est* prennent en charge les deux signets ou approximative de positionnement, cette propriété retourne le nombre exact d’enregistrements dans le jeu d’enregistrements. Cette propriété retourne le nombre exact indépendamment de si le jeu d’enregistrements a été entièrement remplie.

En revanche, si l’objet Recordset ne *pas* prennent en charge les signets ou le positionnement approximatif, l’accès à cette propriété peut être une charge significative sur les ressources. Le vidage se produit parce que tous les enregistrements doivent récupérées et comptées pour renvoyer une valeur RecordCount précise.

- **adBookmark** liées à des signets.
- **adApproxPosition** se rapporte au positionnement approximatif.

> [!NOTE]
> Dans les versions ADO 2.8 et versions antérieures, le fournisseur SQLOLEDB extrait tous les enregistrements lorsqu’un curseur côté serveur est utilisé, en dépit du fait qu’elle retourne **True** pour les deux **prend en charge (adApproxPosition)** et **Prend en charge (adBookmark)**.
  
Le type de curseur de la **Recordset** objet détermine si le nombre d’enregistrements permettre être compté. Le **RecordCount** propriété retourne -1 pour un curseur avant uniquement ; le nombre réel pour une analyse statique ou curseur keyset ; et soit -1 ou le nombre réel pour un curseur dynamique, en fonction de la source de données.
  
## <a name="applies-to"></a>S'applique à

[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi

[Filter et RecordCount, exemple de propriétés (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
[Filter et RecordCount propriétés exemple (VC ++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
[AbsolutePosition, propriété (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
[PageCount, propriété (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
