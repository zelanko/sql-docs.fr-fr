---
description: ReadText, méthode
title: ReadText, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_ReadText
- _Stream::ReadText
helpviewer_keywords:
- ReadText method [ADO]
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c36e4dde000e89b3fe19b258f5d307232b2cb69
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442531"
---
# <a name="readtext-method"></a>ReadText, méthode
Lit le nombre spécifié de caractères à partir d’un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) de texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *NumChars*  
 facultatif. Valeur de **type long** qui spécifie le nombre de caractères à lire à partir du fichier ou une valeur [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) . La valeur par défaut est **adReadAll**.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode **READTEXT** lit un nombre spécifié de caractères, une ligne entière ou le flux entier à partir d’un objet de **flux** et retourne la chaîne résultante.  
  
## <a name="remarks"></a>Notes  
 Si *NUMCHARS* est supérieur au nombre de caractères restants dans le flux, seuls les caractères restants sont retournés. La lecture de la chaîne n’est pas complétée pour correspondre à la longueur spécifiée par *NUMCHARS*. S’il ne reste aucun caractère à lire, une variante dont la valeur est null est retournée. **READTEXT** ne peut pas être utilisé pour lire vers l’arrière.  
  
> [!NOTE]
>  La méthode **READTEXT** est utilisée avec les flux de texte (le[type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Pour les flux binaires (**type** **adTypeBinary**), utilisez [Read](../../../ado/reference/ado-api/read-method.md).  
  
 Les requêtes qui génèrent une grande quantité de données XML retournées par la méthode **READTEXT** de l’objet de flux ADO (ActiveX Data Object) peuvent prendre beaucoup de temps à s’exécuter. Si cette opération est effectuée dans un composant COM+ qui est appelé à partir d’une page ASP, la session de l’utilisateur peut expirer. ADO convertit les données d’objet de flux de l’encodage UTF-8 en Unicode ; la réallocation de mémoire fréquente impliquée dans la conversion d’une grande quantité de données à la fois est assez longue. Pour résoudre le, effectuez des appels répétés à la méthode **READTEXT** de l’objet de commande ADO et spécifiez un plus petit nombre de caractères. Les tests ont montré qu’une valeur équivalant à 128K (131 072) est optimale. Le temps de réponse diminue, car cette valeur est diminuée. Pour plus d’informations, consultez l’article 280067 de la base de connaissances, « PRB : la récupération de documents XML très volumineux à partir de SQL Server 2000 à l’aide de la méthode ReadText de l’objet Stream ADO peut être lente », dans la base de connaissances Microsoft à l’adresse https://support.microsoft.com .  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Read, méthode](../../../ado/reference/ado-api/read-method.md)
