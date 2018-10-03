---
title: WriteText, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3b50db388151de1f5b99d8d9a3f48904e6d7c2c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679887"
---
# <a name="writetext-method"></a>WriteText, méthode
Écrit une chaîne de texte spécifié dans un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Données*  
 Un **chaîne** valeur qui contient le texte en caractères à écrire.  
  
 *Options*  
 Facultatif. Un [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) valeur qui spécifie si un caractère de séparation de ligne doit être écrit à la fin de la chaîne spécifiée.  
  
## <a name="remarks"></a>Notes  
 Chaînes spécifiées sont écrites dans le **Stream** objet sans espaces insérés ni caractères entre chaque chaîne.  
  
 Actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) est définie sur le caractère qui suit les données écrites. Le **WriteText** méthode ne tronque pas le reste des données dans un flux de données. Si vous souhaitez tronquer ces caractères, appelez [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Si vous écrivez après actuel [EOS](../../../ado/reference/ado-api/eos-property.md) position, la [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) de la **Stream** augmente pour contenir les nouveaux caractères, et **EOS** déplace vers le nouveau dernier octet de la **Stream**.  
  
> [!NOTE]
>  Le **WriteText** méthode est utilisée avec des flux de texte ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Pour les flux binaires (**Type** est **adTypeBinary**), utilisez [écrire](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Write, méthode](../../../ado/reference/ado-api/write-method.md)
