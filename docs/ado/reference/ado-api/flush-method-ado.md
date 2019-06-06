---
title: Flush, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6cfc8cf9a618851e3e53b35d54fa1a989ce9c785
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697946"
---
# <a name="flush-method-ado"></a>Flush, méthode (ADO)
Force le contenu de la [Stream](../../../ado/reference/ado-api/stream-object-ado.md) restants dans la mémoire tampon de ADO à l’objet sous-jacent auquel le **Stream** est associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être utilisée pour envoyer le contenu de la mémoire tampon de flux de données à l’objet sous-jacent : par exemple, le nœud ou le fichier représenté par l’URL qui est la source de la **Stream** objet. Cette méthode doit être appelée lorsque vous souhaitez vous assurer que toutes les modifications qui ont été apportées au contenu d’un **Stream** ont été écrits. Toutefois, avec ADO, il n’est pas généralement nécessaire d’appeler **vider**, comme ADO en permanence vide sa mémoire tampon autant que possible en arrière-plan. Modifications apportées au contenu d’un **Stream** sont effectuées automatiquement, non mis en cache jusqu'à ce que **vider** est appelée.  
  
 Fermeture un **Stream** avec la [fermer](../../../ado/reference/ado-api/close-method-ado.md) méthode vide le contenu d’un **Stream** automatiquement ; il n’est pas nécessaire d’appeler explicitement **vider**immédiatement avant **fermer**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
