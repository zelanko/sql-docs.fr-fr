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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc9de1481cc683bddafe2f92959977319600f6a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928631"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Indique si un séparateur de ligne est ajouté à la chaîne écrite dans un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|Valeur par défaut. Écrit la chaîne de texte spécifié (spécifié par le *données* paramètre) à la **Stream** objet.|  
|**adWriteLine**|1|Écrit une chaîne de texte et un caractère de séparation de ligne à un **Stream** objet. Si le [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) propriété n’est pas définie, puis cette commande renvoie une erreur d’exécution.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [WriteText, méthode](../../../ado/reference/ado-api/writetext-method.md)
