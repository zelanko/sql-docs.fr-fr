---
title: StreamWriteEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 586920fc4f7673f9c5e25c92f252013920acaa8d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="streamwriteenum"></a>StreamWriteEnum
Indique si un séparateur de ligne est ajouté à la chaîne écrite dans un [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Valeur par défaut. Écrit la chaîne de texte spécifié (spécifié par le *données* paramètre) pour le **flux** objet.|  
|**adWriteLine**|1|Écrit une chaîne de texte et un caractère de séparation de ligne pour un **flux** objet. Si le [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) propriété n’est pas définie, puis retourne une erreur d’exécution.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [WriteText, méthode](../../../ado/reference/ado-api/writetext-method.md)

