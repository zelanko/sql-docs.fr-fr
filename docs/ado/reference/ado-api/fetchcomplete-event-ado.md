---
description: FetchComplete, événement (ADO)
title: FetchComplete, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ef8df9f6d4ea113d5cca9ad9ffba9c4888776d8
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973350"
---
# <a name="fetchcomplete-event-ado"></a>FetchComplete, événement (ADO)
L’événement **FetchComplete** est appelé une fois que tous les enregistrements d’une longue opération asynchrone ont été récupérés dans le [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pError*  
 Objet d' [erreur](../../../ado/reference/ado-api/error-object.md) . Il décrit l’erreur qui s’est produite si la valeur de **adStatus** est **adStatusErrorsOccurred**; dans le cas contraire, il n’est pas défini.  
  
 *adStatus*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) . Lorsque cet événement est appelé, ce paramètre a la valeur **adStatusOK** si l’opération à l’origine de l’événement s’est déroulée correctement ou **adStatusErrorsOccurred** si l’opération a échoué.  
  
 Avant le retour de cet événement, définissez ce paramètre sur **adStatusUnwantedEvent** pour empêcher les notifications suivantes.  
  
 *pRecordset*  
 Objet **Recordset** . Objet pour lequel les enregistrements ont été récupérés.  
  
## <a name="remarks"></a>Notes  
 Pour utiliser **FetchComplete** avec Microsoft Visual Basic, Visual Basic 6,0 ou version ultérieure est requis.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
