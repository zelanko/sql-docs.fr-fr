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
author: rothja
ms.author: jroth
ms.openlocfilehash: 605fb2e2afbd73a8a5509102ae98f348aad90bcb
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760065"
---
# <a name="getchildren-method-ado"></a>GetChildren, méthode (ADO)
Retourne un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) dont les lignes représentent les enfants d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md)de collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet **Recordset** pour lequel chaque ligne représente un enfant de l’objet **enregistrement** actif. Par exemple, les enfants d’un **enregistrement** qui représente un répertoire sont les fichiers et les sous-répertoires contenus dans le répertoire parent.  
  
## <a name="remarks"></a>Remarques  
 Le fournisseur détermine les colonnes qui existent dans le **jeu d’enregistrements**retourné. Par exemple, un fournisseur de source de document retourne toujours un **jeu d’enregistrements**de ressources.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
