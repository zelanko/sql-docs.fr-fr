---
title: GetRows, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords:
- Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6babeebec1eac78949f0a80eb0701b5b5ba1dcc2
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694840"
---
# <a name="getrows-method-ado"></a>GetRows, méthode (ADO)
Récupère plusieurs enregistrements d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet dans un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Variant** dont la valeur est un tableau à deux dimensions.  
  
#### <a name="parameters"></a>Paramètres  
 *Lignes*  
 Facultatif. Un [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) valeur qui indique le nombre d’enregistrements à récupérer. La valeur par défaut est **adGetRowsRest**.  
  
 *Démarrer*  
 Facultatif. Un **chaîne** valeur ou **Variant** qui prend la valeur de signet pour l’enregistrement à partir duquel le **GetRows** opération doit commencer. Vous pouvez également utiliser un [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) valeur.  
  
 *Fields*  
 Facultatif. Un **Variant** qui représente un seul nom de champ ou position ordinale ou un tableau de noms de champs ou des nombres de la position ordinale. ADO retourne uniquement les données dans ces champs.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **GetRows** méthode pour copier des enregistrements à partir d’un **Recordset** dans un tableau à deux dimensions. Le premier indice identifie le champ et le deuxième identifie le numéro d’enregistrement. Le *tableau* variable est automatiquement dimensionnée à la bonne taille lors la **GetRows** méthode retourne les données.  
  
 Si vous ne spécifiez pas une valeur pour le *lignes* argument, le **GetRows** méthode récupère automatiquement tous les enregistrements dans le **Recordset** objet. Si vous demandez plus d’enregistrements sont disponibles, **GetRows** retourne uniquement le nombre d’enregistrements disponibles.  
  
 Si le **Recordset** objet prend en charge les signets, vous pouvez spécifier à quel enregistrement la **GetRows** méthode doit commencer à récupérer des données en passant la valeur de cet enregistrement [signet](../../../ado/reference/ado-api/bookmark-property-ado.md)propriété dans le *Démarrer* argument.  
  
 Si vous souhaitez limiter les champs qui le **GetRows** retour d’appel, vous pouvez passer un seul nom/numéro ou un tableau de noms de champ/nombres dans la *champs* argument.  
  
 Après avoir appelé **GetRows**, l’enregistrement suivant non lu devient l’enregistrement en cours, ou le [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriété est définie sur **True** s’il n’existe plus aucun enregistrement.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode GetRows, exemple (VB)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [GetRows, exemple de méthode (VC++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
