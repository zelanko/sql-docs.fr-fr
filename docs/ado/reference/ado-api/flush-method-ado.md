---
description: Flush, méthode (ADO)
title: Flush, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a76817a6219a506ef1158e94b7ffbf2fae6f629f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972980"
---
# <a name="flush-method-ado"></a>Flush, méthode (ADO)
Force le contenu du [flux](./stream-object-ado.md) restant dans la mémoire tampon ADO à l’objet sous-jacent auquel le **flux** est associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être utilisée pour envoyer le contenu de la mémoire tampon de flux à l’objet sous-jacent : par exemple, le nœud ou le fichier représenté par l’URL qui est la source de l’objet de **flux** . Cette méthode doit être appelée lorsque vous souhaitez vous assurer que toutes les modifications apportées au contenu d’un **flux** ont été écrites. Toutefois, avec ADO, il n’est généralement pas nécessaire d’appeler **flush**, car ADO vide continuellement sa mémoire tampon en arrière-plan. Les modifications apportées au contenu d’un **flux** sont effectuées automatiquement, et ne sont pas mises en cache tant que le **vidage** n’est pas appelé.  
  
 La fermeture d’un **flux** à l’aide de la méthode [Close](./close-method-ado.md) vide automatiquement le contenu d’un **flux** ; Il n’est pas nécessaire d’appeler explicitement **flush** immédiatement avant la **fermeture**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](./stream-object-ado.md)