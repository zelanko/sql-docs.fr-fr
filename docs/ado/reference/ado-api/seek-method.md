---
title: Seek, méthode | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a96c8054d83fa0ecff4cc3fed3a1227f300f7e2e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765400"
---
# <a name="seek-method"></a>Seek, méthode
Recherche l’index d’un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) pour localiser rapidement la ligne qui correspond aux valeurs spécifiées et modifie la position de ligne actuelle en cette ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Paramètres  
 *KeyValues*  
 Tableau de valeurs de **type Variant** . Un index se compose d’une ou plusieurs colonnes et le tableau contient une valeur à comparer à chaque colonne correspondante.  
  
 *SeekOption*  
 Valeur de [SeekEnum](../../../ado/reference/ado-api/seekenum.md) qui spécifie le type de comparaison à effectuer entre les colonnes de l’index et les *valeurs de KeyValues*correspondantes.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la méthode **Seek** conjointement à la propriété [index](../../../ado/reference/ado-api/index-property.md) si le fournisseur sous-jacent prend en charge les index sur l’objet **Recordset** . Utilisez la méthode [supports](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** pour déterminer si le fournisseur sous-jacent prend en charge la **recherche**, et la méthode **prend en charge (adIndex)** pour déterminer si le fournisseur prend en charge les index. (Par exemple, le [fournisseur de OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) prend en charge la **recherche** et l' **indexation**.)  
  
 Si la **recherche** ne trouve pas la ligne souhaitée, aucune erreur ne se produit et la ligne est positionnée à la fin de l’ensemble d' **enregistrements**. Définissez la propriété **index** sur l’index souhaité avant d’exécuter cette méthode.  
  
 Cette méthode est prise en charge uniquement avec les curseurs côté serveur. Seek n’est pas pris en charge lorsque la valeur de la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) de l’objet **Recordset** est **adUseClient**.  
  
 Cette méthode peut uniquement être utilisée lorsque l’objet **Recordset** a été ouvert avec une valeur [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) de **adCmdTableDirect**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Seek et index, exemple de propriété (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Méthode Seek et index, exemple de propriété (VC + +)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find, méthode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index, propriété](../../../ado/reference/ado-api/index-property.md)
