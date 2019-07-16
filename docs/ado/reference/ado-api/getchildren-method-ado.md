---
title: GetChildren, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84f1a2f7a80e17571f1b8ad3e63db640fb58dc19
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932509"
---
# <a name="getchildren-method-ado"></a>GetChildren, méthode (ADO)
Retourne un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dont les lignes représentent les enfants d’une collection [enregistrement](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un **Recordset** objet pour lequel chaque ligne représente un enfant de l’actuel **enregistrement** objet. Par exemple, les enfants d’un **enregistrement** que représente un répertoire, sont les fichiers et sous-répertoires contenus dans le répertoire parent.  
  
## <a name="remarks"></a>Notes  
 Le fournisseur détermine les colonnes qui figureront dans retourné **Recordset**. Par exemple, un fournisseur de source de document retourne toujours une ressource **Recordset**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
