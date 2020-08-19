---
description: GetChildren, méthode (ADO)
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
ms.openlocfilehash: 906c20d19143f4f1e8fe0b6c1e91585893acfa5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443581"
---
# <a name="getchildren-method-ado"></a>GetChildren, méthode (ADO)
Retourne un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) dont les lignes représentent les enfants d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md)de collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet **Recordset** pour lequel chaque ligne représente un enfant de l’objet **enregistrement** actif. Par exemple, les enfants d’un **enregistrement** qui représente un répertoire sont les fichiers et les sous-répertoires contenus dans le répertoire parent.  
  
## <a name="remarks"></a>Notes  
 Le fournisseur détermine les colonnes qui existent dans le **jeu d’enregistrements**retourné. Par exemple, un fournisseur de source de document retourne toujours un **jeu d’enregistrements**de ressources.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::
