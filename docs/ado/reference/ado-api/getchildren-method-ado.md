---
title: "GetChildren, méthode (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords: GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fff51cb110366031907d8aeaa272f72eb7dc0fd2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="getchildren-method-ado"></a>GetChildren, méthode (ADO)
Retourne un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dont les lignes représentent les enfants d’une collection [enregistrement](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **Recordset** objet pour lequel chaque ligne représente un enfant d’actuel **enregistrement** objet. Par exemple, les enfants d’un **enregistrement** que représente un répertoire, sont les fichiers et sous-répertoires contenus dans le répertoire parent.  
  
## <a name="remarks"></a>Notes   
 Le fournisseur détermine les colonnes qui figureront dans retourné **Recordset**. Par exemple, un fournisseur de source de document retourne toujours une ressource **Recordset**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
