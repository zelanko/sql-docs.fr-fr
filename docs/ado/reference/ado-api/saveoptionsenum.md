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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3423d215fa4a52286509769bb2ac0b75d2283a02
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755839"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Spécifie si un fichier doit être créé ou remplacé lors de l’enregistrement à partir d’un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) . Les valeurs peuvent être **adSaveCreateNotExist** ou **adSaveCreateOverWrite**.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Par défaut. Crée un nouveau fichier si le fichier spécifié par le paramètre de *nom* de fichier n’existe pas déjà.|  
|**adSaveCreateOverWrite**|2|Remplace le fichier par les données de l’objet de **flux** actuellement ouvert, si le fichier spécifié par le paramètre *filename* existe déjà. Si le fichier spécifié par le paramètre *filename* n’existe pas, un nouveau fichier est créé.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [SaveToFile, méthode](../../../ado/reference/ado-api/savetofile-method.md)
