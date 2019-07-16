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
ms.openlocfilehash: 738f4cece8cf2355c12c0de4ac42314152c6370a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67921441"
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
