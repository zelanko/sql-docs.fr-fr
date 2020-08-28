---
description: GetChildren, méthode (ADO)
title: GetChildren, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: ea59a94f095a438be8fc7009a58179d488af20a2
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972830"
---
# <a name="getchildren-method-ado"></a>GetChildren, méthode (ADO)
Retourne un [jeu d’enregistrements](./recordset-object-ado.md) dont les lignes représentent les enfants d’un [enregistrement](./record-object-ado.md)de collection.  
  
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
        [Record, objet (ADO)](./record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset, objet (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::