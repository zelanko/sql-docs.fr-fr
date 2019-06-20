---
title: SaveToFile, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1b3a94fddf1ac439096e2e0106fb2becb79249c7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711335"
---
# <a name="savetofile-method"></a>SaveToFile, méthode
Enregistre le contenu binaire d’un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) dans un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Paramètres  
 *FileName*  
 Un **chaîne** valeur qui contient le nom qualifié complet du fichier dans lequel le contenu de la **Stream** sera enregistré. Vous pouvez enregistrer dans n’importe quel emplacement local valide ou n’importe quel emplacement que vous avez accès via une valeur UNC.  
  
 *SaveOptions*  
 Un [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) valeur qui spécifie si un nouveau fichier doit être créé par **SaveToFile**, s’il n’existe pas déjà. Valeur par défaut est **adSaveCreateNotExists**. Avec ces options, vous pouvez spécifier qu’une erreur se produit si le fichier spécifié n’existe pas. Vous pouvez également préciser que **SaveToFile** remplace le contenu actuel d’un fichier existant.  
  
> [!NOTE]
>  Si vous remplacez un fichier existant (lorsque **valeur adSaveCreateOverwrite** est défini), **SaveToFile** tronque tous les octets à partir du fichier existant d’origine qui suivent la nouvelle [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Notes  
 **SaveToFile** peut servir à copier le contenu d’un **Stream** objet dans un fichier local. Il n’existe aucune modification dans le contenu ou les propriétés de la **Stream** objet. Le **Stream** objet doit être ouvert avant d’appeler **SaveToFile**.  
  
 Cette méthode ne modifie pas l’association de la **Stream** objet et sa source sous-jacente. Le **Stream** objet sera toujours associé à l’URL d’origine ou **enregistrement** qui a été source de son ouverture.  
  
 Après un **SaveToFile** opération, la position actuelle ([Position](../../../ado/reference/ado-api/position-property-ado.md)) dans le flux est définie au début du flux (0).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Open, méthode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
