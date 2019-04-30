---
title: Comparabilité pour IRowsetFind | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability [ODBC]
ms.assetid: 7d148b56-9bbe-4e55-b31f-43f115705402
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9aa8cb118a84bca1d37bdd409055b21d1d11552
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233028"
---
# <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind
  Pour les types date/time uniquement, IRowsetFind prend en charge les comparaisons suivantes :  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 Si une autre comparaison est tentée, DB_E_BADCOMPAREOP est retourné. Ce comportement est conforme à la spécification OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
