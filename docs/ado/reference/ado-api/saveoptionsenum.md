---
title: SaveOptionsEnum | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebd08388e2b658c6a4b5d85000d48dd4fe77c671
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Spécifie si un fichier doit être créé ou remplacé lors de l’enregistrement d’un [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet. Les valeurs peuvent être **adSaveCreateNotExist** ou **valeur adSaveCreateOverWrite**...  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Valeur par défaut. Crée un nouveau fichier si le fichier spécifié par le *nom de fichier* paramètre n’existe pas déjà.|  
|**adSaveCreateOverWrite**|2|Remplace le fichier avec les données actuellement ouvert **flux** de l’objet, si le fichier spécifié par le *nom de fichier* paramètre existe déjà. Si le fichier spécifié par le *nom de fichier* paramètre n’existe pas, un nouveau fichier est créé.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [SaveToFile, méthode](../../../ado/reference/ado-api/savetofile-method.md)
