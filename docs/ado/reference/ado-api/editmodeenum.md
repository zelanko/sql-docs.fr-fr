---
title: EditModeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a8c4ddb27bbc6831095062af5491fb501b6d5b7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933047"
---
# <a name="editmodeenum"></a>EditModeEnum
Spécifie l’état de modification d’un enregistrement.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Indique qu’aucune opération de modification n’est en cours.|  
|**adEditInProgress**|1|Indique que les données de l’enregistrement en cours ont été modifiées mais pas enregistrées.|  
|**adEditAdd**|2|Indique que la méthode [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) a été appelée et que l’enregistrement actif dans la mémoire tampon de copie est un nouvel enregistrement qui n’a pas été enregistré dans la base de données.|  
|**adEditDelete**|4|Indique que l’enregistrement en cours a été supprimé.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>S'applique à  
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)
