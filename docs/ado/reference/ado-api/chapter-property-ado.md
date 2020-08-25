---
description: Chapter, propriété (ADO)
title: Chapter, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords:
- Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
author: rothja
ms.author: jroth
ms.openlocfilehash: 04469dc7cc888a167135ad18a77469200614e925
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776298"
---
# <a name="chapter-property-ado"></a>Chapter, propriété (ADO)
Obtient ou définit un objet OLE DB **chapitre** à partir de/sur un objet d' [interface ADORecordsetConstruction](./adorecordsetconstruction-interface.md) . Lorsque vous utilisez **put_Chapter** pour définir l’objet **Chapter** , un sous-ensemble de lignes est converti en objet [objet Recordset](./recordset-object-ado.md) ADO. Cela définit le chapitre actuel de l’objet **rowset**. Cette propriété est en lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Paramètres  
 *plChapter*  
 Pointeur vers le handle d’un chapitre.  
  
 *LChapter*  
 Handle d’un chapitre.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété retourne les valeurs HRESULT standard, y compris S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordsetConstruction, interface](./adorecordsetconstruction-interface.md)