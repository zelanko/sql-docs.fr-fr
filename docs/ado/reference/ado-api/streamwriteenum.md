---
description: StreamWriteEnum
title: StreamWriteEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: c09a15f5c5aba9d36f038304b68cc1e64112ade3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988440"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Spécifie si un séparateur de ligne est ajouté à la chaîne écrite dans un objet de [flux](./stream-object-ado.md) .  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Par défaut. Écrit la chaîne de texte spécifiée (spécifiée par le paramètre de *données* ) dans l’objet de **flux** .|  
|**adWriteLine**|1|Écrit une chaîne de texte et un caractère de séparation de ligne dans un objet de **flux** . Si la propriété [LineSeparator](./lineseparator-property-ado.md) n’est pas définie, elle retourne une erreur d’exécution.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [WriteText, méthode](./writetext-method.md)