---
title: Déterminer le Mode Édition | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22e63bad49586bbbc1a5616114055779cd3ea041
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925544"
---
# <a name="determining-edit-mode"></a>Détermination du mode d’édition
ADO gère une mémoire tampon d’édition associé à l’enregistrement actif. Le **EditMode** propriété indique si les modifications ont été apportées à cette mémoire tampon ou si un nouvel enregistrement a été créé. Utilisez **EditMode** pour déterminer l’état de modification de l’enregistrement en cours. Vous pouvez tester pour les modifications en attente si un processus de modification a été interrompu et déterminer s’il faut utiliser le **mise à jour** ou **CancelUpdate** (méthode).  
  
 **EditMode** retourne une de la **EditModeEnum** constantes, qui sont répertoriées dans le tableau suivant.  
  
|Constante|Description|  
|--------------|-----------------|  
|**adEditNone**|Indique qu’aucune opération de modification n’est en cours.|  
|**adEditInProgress**|Indique que les données dans l’enregistrement actif ont été modifiées mais ne pas enregistrées.|  
|**adEditAdd**|Indique que le **AddNew** méthode a été appelée, et l’enregistrement actif dans la mémoire tampon de copie est un nouvel enregistrement qui n’a pas été enregistré dans la base de données.|  
|**adEditDelete**|Indique que l’enregistrement en cours a été supprimé.|  
  
 **EditMode** peut retourner une valeur valide uniquement s’il existe un enregistrement en cours. **EditMode** retournera une erreur si **BOF** ou **EOF** est **True** ou si l’enregistrement en cours a été supprimé.
