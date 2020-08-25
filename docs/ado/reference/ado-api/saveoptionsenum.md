---
description: SaveOptionsEnum
title: SaveOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
author: rothja
ms.author: jroth
ms.openlocfilehash: edac11f61b003307703ec13daed8022b8af31bae
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777558"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Spécifie si un fichier doit être créé ou remplacé lors de l’enregistrement à partir d’un objet de [flux](./stream-object-ado.md) . Les valeurs peuvent être **adSaveCreateNotExist** ou **adSaveCreateOverWrite**.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Par défaut. Crée un nouveau fichier si le fichier spécifié par le paramètre de *nom* de fichier n’existe pas déjà.|  
|**adSaveCreateOverWrite**|2|Remplace le fichier par les données de l’objet de **flux** actuellement ouvert, si le fichier spécifié par le paramètre *filename* existe déjà. Si le fichier spécifié par le paramètre *filename* n’existe pas, un nouveau fichier est créé.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [SaveToFile, méthode](./savetofile-method.md)