---
title: FetchProgress, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f47fb473d0120c124fd07fbb0b30bdecf991926f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682151"
---
# <a name="fetchprogress-event-ado"></a>FetchProgress, événement (ADO)
Le **FetchProgress**événement est régulièrement appelé pendant une longue opération asynchrone pour signaler le nombre de lignes déjà extraites dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Progression*  
 Un **Long** valeur indiquant le nombre d’enregistrements qui ont actuellement été récupérées à l’opération de récupération.  
  
 *MaxProgress*  
 Un **Long** valeur indiquant le nombre maximal d’enregistrements doit être récupéré.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 *pRecordset*  
 Un **Recordset** objet qui est l’objet pour lequel les enregistrements sont extraits.  
  
## <a name="remarks"></a>Notes  
 Lors de l’utilisation **FetchProgress** avec un enfant **Recordset**, n’oubliez pas que le *progression* et *MaxProgress* dérivées des valeurs de paramètre sous-jacent [Service de curseur](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) ensemble de lignes. Les valeurs retournées représentent le nombre total d’enregistrements dans l’ensemble de lignes sous-jacent, pas seulement le nombre d’enregistrements dans le chapitre actuel.  
  
> [!NOTE]
>  Pour utiliser **FetchProgress** avec Microsoft Visual Basic, Visual Basic 6.0 ou version ultérieure est requis.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
