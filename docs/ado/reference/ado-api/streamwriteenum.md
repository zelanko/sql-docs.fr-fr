---
title: StreamWriteEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 479bc032cf779752f11dccca73ee56fc05a8ebdd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759565"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Spécifie si un séparateur de ligne est ajouté à la chaîne écrite dans un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Par défaut. Écrit la chaîne de texte spécifiée (spécifiée par le paramètre de *données* ) dans l’objet de **flux** .|  
|**adWriteLine**|1|Écrit une chaîne de texte et un caractère de séparation de ligne dans un objet de **flux** . Si la propriété [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) n’est pas définie, elle retourne une erreur d’exécution.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [WriteText, méthode](../../../ado/reference/ado-api/writetext-method.md)
