---
description: StreamWriteEnum
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
ms.openlocfilehash: 939de5306982ab2e369fce0648e477cac5f48cb8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441791"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Spécifie si un séparateur de ligne est ajouté à la chaîne écrite dans un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Par défaut. Écrit la chaîne de texte spécifiée (spécifiée par le paramètre de *données* ) dans l’objet de **flux** .|  
|**adWriteLine**|1|Écrit une chaîne de texte et un caractère de séparation de ligne dans un objet de **flux** . Si la propriété [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) n’est pas définie, elle retourne une erreur d’exécution.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [WriteText, méthode](../../../ado/reference/ado-api/writetext-method.md)
