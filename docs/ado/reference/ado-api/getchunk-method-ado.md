---
title: GetChunk, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c5dc09043d780c2a743059773eed56e16a799bf5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694948"
---
# <a name="getchunk-method-ado"></a>GetChunk, méthode (ADO)
Retourne l’ensemble ou une partie du contenu d’un texte de grande taille ou les données binaires [champ](../../../ado/reference/ado-api/field-object.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Variant**.  
  
#### <a name="parameters"></a>Paramètres  
 *Taille*  
 Un **Long** expression qui est égale au nombre d’octets ou de caractères que vous souhaitez récupérer.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **GetChunk** méthode sur un **champ** objet à récupérer tout ou partie de ses données binaires ou caractères de long. Dans les situations où la mémoire système est limitée, vous pouvez utiliser la **GetChunk** méthode pour manipuler les valeurs de type long dans les parties, plutôt que dans leur intégralité.  
  
 Les données qui un **GetChunk** appel retourne est affectée à *variable*. Si *taille* est supérieur aux données restantes, le **GetChunk** méthode retourne uniquement les données restantes sans remplissage *variable* avec des espaces vides. Si le champ est vide, le **GetChunk** méthode retourne une valeur null.  
  
 Chaque **GetChunk** appel récupère les données en commençant à partir de laquelle le précédent **GetChunk** appel s’est arrêté. Toutefois, si vous récupérez des données à partir d’un champ et que vous définissez ou lisez la valeur d’un autre champ dans l’enregistrement actif, ADO part du principe que vous avez terminé la récupération des données à partir du premier champ. Si vous appelez le **GetChunk** méthode sur le premier champ, ADO interprète l’appel en tant que nouvelle **GetChunk** opération et commence à lire à partir du début des données. L’accès à d’autres champs [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) les objets qui ne sont pas des clones du premier **Recordset** n’interrompt pas les objets **GetChunk** operations.  
  
 Si le **adFldLong** bit dans le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété d’un **champ** objet est défini sur **True**, vous pouvez utiliser le **GetChunk**  (méthode) pour ce champ.  
  
 S’il n’existe aucun enregistrement actif lorsque vous utilisez le **GetChunk** méthode sur un **champ** de l’objet, l’erreur 3021 (aucun enregistrement actif) survient.  
  
> [!NOTE]
>  Le **GetChunk** méthode ne fonctionne pas sur **champ** objets d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet. Il n’effectue aucune opération et entraîne une erreur d’exécution.  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AppendChunk et GetChunk, exemple de méthodes (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk et GetChunk, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [AppendChunk, méthode (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Attributes, propriété (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
