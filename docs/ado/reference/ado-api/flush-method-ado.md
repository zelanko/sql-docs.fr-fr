---
title: "Flush (méthode) (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94a5e1ced6f0b302253298dcbfb9cd345b9f5bfe
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="flush-method-ado"></a>Flush (méthode) (ADO)
Force le contenu de la [flux](../../../ado/reference/ado-api/stream-object-ado.md) restants dans la mémoire tampon d’ADO à l’objet sous-jacent avec lequel le **flux** est associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être utilisée pour envoyer le contenu de la mémoire tampon de flux de données à l’objet sous-jacent : par exemple, le nœud ou le fichier représenté par l’URL qui est la source de la **flux** objet. Cette méthode doit être appelée lorsque vous souhaitez vous assurer que toutes les modifications qui ont été apportées au contenu d’un **flux** ont été écrits. Toutefois, avec ADO il est généralement pas nécessaire d’appeler **vider**, comme ADO vide continuellement sa mémoire tampon autant que possible en arrière-plan. Modifications du contenu d’un **flux** sont effectuées automatiquement, non mis en cache jusqu'à ce que **vider** est appelée.  
  
 Fermeture un **flux** avec la [fermer](../../../ado/reference/ado-api/close-method-ado.md) méthode vide le contenu d’un **flux** automatiquement ; il n’est pas nécessaire d’appeler explicitement **vider**immédiatement avant **fermer**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
