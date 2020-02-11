---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 807a8d7e5757a2caf76f100a1ae51c4a8a3f4e98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931145"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Spécifie si un fichier doit être créé ou remplacé lors de l’enregistrement à partir d’un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) . Les valeurs peuvent être **adSaveCreateNotExist** ou **adSaveCreateOverWrite**.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|valeur par défaut. Crée un nouveau fichier si le fichier spécifié par le paramètre de *nom* de fichier n’existe pas déjà.|  
|**adSaveCreateOverWrite**|2|Remplace le fichier par les données de l’objet de **flux** actuellement ouvert, si le fichier spécifié par le paramètre *filename* existe déjà. Si le fichier spécifié par le paramètre *filename* n’existe pas, un nouveau fichier est créé.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [SaveToFile, méthode](../../../ado/reference/ado-api/savetofile-method.md)
