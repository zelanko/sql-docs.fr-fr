---
title: "FetchProgress, événement (ADO) | Documents Microsoft"
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
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords: FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 990e5bbe3a203cd48c34c6153a9ee0ca8e678758
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="fetchprogress-event-ado"></a>FetchProgress, événement (ADO)
Le **FetchProgress**événement est appelé régulièrement pendant une longue opération asynchrone pour signaler le nombre de lignes actuellement ont été récupéré dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Progression*  
 A **Long** valeur indiquant le nombre d’enregistrements qui ont déjà extraits par l’opération d’extraction.  
  
 *MaxProgress*  
 A **Long** prévu de valeur qui indique le nombre maximal d’enregistrements à récupérer.  
  
 *N'*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 *Connection*  
 A **Recordset** objet qui est l’objet pour lequel les enregistrements sont récupérés.  
  
## <a name="remarks"></a>Notes  
 Lors de l’utilisation **FetchProgress** avec un enfant **Recordset**, gardez à l’esprit que le *progression* et *MaxProgress* dérivées des valeurs de paramètre sous-jacent [Service de curseur](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) ensemble de lignes. Les valeurs retournées représentent le nombre total d’enregistrements dans l’ensemble de lignes sous-jacent, et pas seulement le nombre d’enregistrements dans le chapitre actuel.  
  
> [!NOTE]
>  Pour utiliser **FetchProgress** avec Microsoft Visual Basic, Visual Basic 6.0 ou version ultérieure est requis.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
