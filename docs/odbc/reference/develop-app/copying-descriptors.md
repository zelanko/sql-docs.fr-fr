---
title: Copie des descripteurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d41cd744d39113c556c4ee8bc17411b7992e596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002138"
---
# <a name="copying-descriptors"></a>Copie de descripteurs
La fonction **SQLCopyDesc** est appelée pour copier les champs d’un descripteur vers un autre descripteur. Les champs peuvent être copiés uniquement vers un descripteur d’application ou un IPD, mais pas vers un IRD. Les champs peuvent être copiés à partir de n’importe quel type de descripteur. Seuls les champs définis pour les descripteurs source et cible sont copiés. **SQLCopyDesc** ne copie pas le champ SQL_DESC_ALLOC_TYPE, car le type d’allocation d’un descripteur ne peut pas être modifié. Les champs copiés remplacent les champs existants.  
  
 Un ARD sur un descripteur d’instruction peut servir de APD sur un autre descripteur d’instruction. Cela permet à une application de copier des lignes entre des tables sans copier les données au niveau de l’application. Pour ce faire, un descripteur de ligne décrivant une ligne extraite d’une table est réutilisé comme descripteur de paramètre pour un paramètre dans une instruction INSERT. Le type d’informations de SQL_MAX_CONCURRENT_ACTIVITIES doit être supérieur à 1 pour que cette opération aboutisse.
