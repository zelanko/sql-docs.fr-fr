---
title: "La méthode de recherche | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords: Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d94cf588916667e2cf82992b6a3ac6b601e8f84
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="seek-method"></a>La méthode de recherche
Recherche l’index d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) pour localiser rapidement la ligne qui correspond aux valeurs spécifiées et la position de ligne en cours à cette ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Paramètres  
 *KeyValues*  
 Un tableau de **Variant** valeurs. Un index se compose d’une ou plusieurs colonnes et le tableau contient une valeur à comparer à chaque colonne correspondante.  
  
 *SeekOption*  
 A [SeekEnum](../../../ado/reference/ado-api/seekenum.md) valeur qui spécifie le type de comparaison à effectuer entre les colonnes de l’index et correspondants *KeyValues*.  
  
## <a name="remarks"></a>Notes   
 Utilisez le **recherche** méthode conjointement avec le [Index](../../../ado/reference/ado-api/index-property.md) propriété si le fournisseur sous-jacent prend en charge les index sur la **Recordset** objet. Utilisez le [prend en charge](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** méthode pour déterminer si le fournisseur sous-jacent prend en charge **recherche**et le **supports (adIndex)** méthode pour déterminer si le fournisseur prend en charge les index. (Par exemple, le [fournisseur OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) prend en charge **recherche** et **Index**.)  
  
 Si **recherche** n’a pas trouvé la ligne requise, aucune erreur ne se produit et la ligne est placé à la fin de la **Recordset**. Définir le **Index** index à la propriété souhaitée avant l’exécution de cette méthode.  
  
 Cette méthode est prise en charge uniquement avec les curseurs côté serveur. Seek n’est pas pris en charge lorsque le **Recordset** l’objet [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) valeur de propriété est **adUseClient**.  
  
 Cette méthode peut uniquement être utilisé lorsque le **Recordset** objet a été ouverte avec un [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeur **adCmdTableDirect**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche la méthode et les Index, propriété-Exemple (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Recherche la méthode et les Index, propriété-Exemple (VC ++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find (méthode) (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index, propriété](../../../ado/reference/ado-api/index-property.md)
