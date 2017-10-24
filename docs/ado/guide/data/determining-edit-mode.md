---
title: "Déterminer le Mode Édition | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ca4098a61984e009a2874fdca55d898938ce702d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="determining-edit-mode"></a>Déterminer le Mode d’édition
ADO gère un tampon d’édition associé à l’enregistrement actif. Le **EditMode** propriété indique si les modifications ont été apportées à cette mémoire tampon ou si un enregistrement a été créé. Utilisez **EditMode** pour déterminer l’état de modification de l’enregistrement actif. Vous pouvez tester les modifications en attente si un processus de modification a été interrompu et déterminer si vous devez utiliser le **mise à jour** ou **CancelUpdate** (méthode).  
  
 **EditMode** renvoie un de le **EditModeEnum** constantes, qui sont répertoriées dans le tableau suivant.  
  
|Constante| Description|  
|--------------|-----------------|  
|**adEditNone**|Indique qu’aucune opération de modification n’est en cours.|  
|**adEditInProgress**|Indique que les données dans l’enregistrement actif ont été modifiées mais ne pas enregistrées.|  
|**adEditAdd**|Indique que le **AddNew** méthode a été appelée, et l’enregistrement actif dans le tampon de copie est un nouvel enregistrement qui n’a pas été enregistré dans la base de données.|  
|**adEditDelete**|Indique que l’enregistrement en cours a été supprimé.|  
  
 **EditMode** peut retourner une valeur valide uniquement si un enregistrement actif. **EditMode** retournera une erreur si **BOF** ou **EOF** est **True** ou si l’enregistrement actif a été supprimé.

