---
title: ADCPROP_AUTORECALC_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c3c085a09b800bb5dd6ce02ca3fa2d570b74190e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718583"
---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
Spécifie à quel moment le [MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) fournisseur recalcule les colonnes calculées et agrégées dans un Recordset hiérarchique.  
  
 Ces constantes sont utilisées uniquement avec la **MSDataShape** fournisseur et le **Recordset** »**le recalcul automatique**« propriété dynamique, qui est référencée dans le [ADO Index des propriétés dynamiques](../../../ado/reference/ado-api/ado-dynamic-property-index.md) et documenté dans le [Service de curseur Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) ou [Microsoft Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) documentation.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|Valeur par défaut. Recalcule chaque fois que le **MSDataShape** fournisseur détermine les valeurs dépendent les colonnes calculées ont changé.|  
|**adRecalcUpFront**|0|Calcule uniquement à la première construction le hiérarchique **Recordset**.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.
