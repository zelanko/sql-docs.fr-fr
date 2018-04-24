---
title: ADCPROP_AUTORECALC_ENUM | Documents Microsoft
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
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5cac0bdaf0980913cbbcbde4147bafece3de8a0a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
Spécifie à quel moment le [MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) fournisseur recalcule les colonnes regroupées et calculées dans un objet Recordset hiérarchique.  
  
 Ces constantes sont utilisées uniquement avec la **MSDataShape** fournisseur et le **Recordset** »**le de recalcul automatique**« propriété dynamique, qui est référencée dans le [ADO Index des propriétés dynamiques](../../../ado/reference/ado-api/ado-dynamic-property-index.md) et documenté dans le [le Service de curseur Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) ou [Service de mise en forme des données Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) documentation.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|Valeur par défaut. Recalcule chaque fois que le **MSDataShape** fournisseur détermine des valeurs modifiées dont dépendent les colonnes calculées.|  
|**adRecalcUpFront**|0|Calcule uniquement lors de la génération initialement le hiérarchique **Recordset**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.
