---
title: La méthode de recherche | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3e2ee81ac2ede53eb4fdbcfe8d3b5987db96f1ad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917016"
---
# <a name="seek-method"></a>Seek, méthode
Recherche l’index d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) pour localiser rapidement la ligne qui correspond aux valeurs spécifiées et la position de ligne actuelle pour cette ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Paramètres  
 *KeyValues*  
 Un tableau de **Variant** valeurs. Un index se compose d’une ou plusieurs colonnes et le tableau contient une valeur à comparer à chaque colonne correspondante.  
  
 *SeekOption*  
 Un [SeekEnum](../../../ado/reference/ado-api/seekenum.md) valeur qui spécifie le type de comparaison à effectuer entre les colonnes de l’index et le correspondantes *KeyValues*.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **recherche** méthode conjointement avec le [Index](../../../ado/reference/ado-api/index-property.md) propriété si le fournisseur sous-jacent prend en charge les index sur la **Recordset** objet. Utilisez le [prend en charge](../../../ado/reference/ado-api/supports-method.md) **(adSeek)** méthode pour déterminer si le fournisseur sous-jacent prend en charge **recherche**et le **supports (adIndex)** méthode pour déterminer si le fournisseur prend en charge les index. (Par exemple, le [fournisseur OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) prend en charge **recherche** et **Index**.)  
  
 Si **recherche** n’a pas de rechercher la ligne souhaitée, aucune erreur ne se produit et la ligne est placé à la fin de la **Recordset**. Définir le **Index** index à la propriété souhaitée avant d’exécuter cette méthode.  
  
 Cette méthode est prise en charge uniquement avec les curseurs côté serveur. Seek n’est pas pris en charge lorsque le **Recordset** l’objet [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) valeur de propriété est **adUseClient**.  
  
 Cette méthode peut uniquement être utilisé lorsque le **Recordset** objet a été ouvert avec un [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeur **adCmdTableDirect**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Seek (méthode) et Index, exemple de propriété (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Seek (méthode) et Index, propriété-Exemple (VC ++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Rechercher, méthode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index, propriété](../../../ado/reference/ado-api/index-property.md)
