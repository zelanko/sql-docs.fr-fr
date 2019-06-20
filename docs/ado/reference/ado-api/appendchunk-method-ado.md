---
title: AppendChunk, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e4b7b7a97af9059e944d2d2d9e7d19afedf4234d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696417"
---
# <a name="appendchunk-method-ado"></a>AppendChunk, méthode (ADO)
Ajoute des données à un texte de grande taille ou les données binaires [champ](../../../ado/reference/ado-api/field-object.md), ou à un [paramètre](../../../ado/reference/ado-api/parameter-object.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Paramètres  
 *object*  
 Un **champ** ou **paramètre** objet.  
  
 *Data*  
 Un **Variant** qui contient les données à ajouter à l’objet.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **AppendChunk** méthode sur un **champ** ou **paramètre** objet à remplir avec des données binaires ou caractères de long. Dans les situations où la mémoire système est limitée, vous pouvez utiliser la **AppendChunk** méthode pour manipuler les valeurs de type long dans les parties plutôt que dans leur intégralité.  
  
## <a name="field"></a>Champ  
 Si le **adFldLong** bit dans le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété d’un **champ** objet est défini sur **true**, vous pouvez utiliser le  **AppendChunk** méthode pour ce champ.  
  
 La première **AppendChunk** appeler sur un **champ** objet écrit des données dans le champ, en remplaçant toutes les données existantes. Ultérieures **AppendChunk** appels ajoutent aux données existantes. Si vous ajoutez des données à un seul champ, et ensuite de définir ou de lire la valeur d’un autre champ dans l’enregistrement actif, ADO suppose que vous avez terminé d’ajouter des données dans le premier champ. Si vous appelez le **AppendChunk** méthode sur le premier champ, ADO interprète l’appel en tant que nouvelle **AppendChunk** opération et remplace les données existantes. L’accès à d’autres champs [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) les objets qui ne sont pas des clones du premier **Recordset** n’interrompt pas les objets **AppendChunk** operations.  
  
 S’il n’existe aucun enregistrement actif lorsque vous appelez **AppendChunk** sur un **champ** de l’objet, une erreur se produit.  
  
> [!NOTE]
>  Le **AppendChunk** méthode ne fonctionne pas sur **champ** objets d’un [enregistrement objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md) objet. Il n’effectue aucune opération et entraîne une erreur d’exécution.  
  
## <a name="parameter"></a>Paramètre  
 Si le **adParamLong** bit dans le **attributs** propriété d’un **paramètre** objet est défini sur **true**, vous pouvez utiliser le  **AppendChunk** méthode pour ce paramètre.  
  
 La première **AppendChunk** appeler sur un **paramètre** objet écrit des données dans le paramètre, en remplaçant toutes les données existantes. Ultérieures **AppendChunk** appelle sur un **paramètre** d’ajout d’objet paramètre aux données existantes. Un **AppendChunk** appel qui passe une valeur null annule toutes les données de paramètre.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Field, objet](../../../ado/reference/ado-api/field-object.md)|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [AppendChunk et GetChunk, exemple de méthodes (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk et GetChunk, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [GetChunk, méthode (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
