---
title: EditModeEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: EditModeEnum
helpviewer_keywords: EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9d1a7543dd09644bbda76a7b3f787479deb6a3e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="editmodeenum"></a>EditModeEnum
Spécifie l’état de modification d’un enregistrement.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Indique qu’aucune opération de modification n’est en cours.|  
|**adEditInProgress**|1|Indique que les données dans l’enregistrement actif ont été modifiées mais ne pas enregistrées.|  
|**adEditAdd**|2|Indique que le [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) méthode a été appelée, et l’enregistrement actif dans le tampon de copie est un nouvel enregistrement qui n’a pas été enregistré dans la base de données.|  
|**adEditDelete**|4|Indique que l’enregistrement en cours a été supprimé.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>S'applique à  
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)
