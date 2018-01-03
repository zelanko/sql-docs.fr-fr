---
title: SaveOptionsEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: SaveOptionsEnum
helpviewer_keywords: SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3830c052e6bf50bb8f85392f509f44e702639024
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Spécifie si un fichier doit être créé ou remplacé lors de l’enregistrement d’un [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet. Les valeurs peuvent être **adSaveCreateNotExist** ou **valeur adSaveCreateOverWrite**...  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**| 1|Valeur par défaut. Crée un nouveau fichier si le fichier spécifié par le *nom de fichier* paramètre n’existe pas déjà.|  
|**valeur adSaveCreateOverWrite**|2|Remplace le fichier avec les données actuellement ouvert **flux** de l’objet, si le fichier spécifié par le *nom de fichier* paramètre existe déjà. Si le fichier spécifié par le *nom de fichier* paramètre n’existe pas, un nouveau fichier est créé.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [SaveToFile, méthode](../../../ado/reference/ado-api/savetofile-method.md)
