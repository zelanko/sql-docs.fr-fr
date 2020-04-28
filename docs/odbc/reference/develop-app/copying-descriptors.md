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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e2e5897afc3673a21396e256df04d25008c8cdf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301668"
---
# <a name="copying-descriptors"></a>Copie de descripteurs
La fonction **SQLCopyDesc** est appelée pour copier les champs d’un descripteur vers un autre descripteur. Les champs peuvent être copiés uniquement vers un descripteur d’application ou un IPD, mais pas vers un IRD. Les champs peuvent être copiés à partir de n’importe quel type de descripteur. Seuls les champs définis pour les descripteurs source et cible sont copiés. **SQLCopyDesc** ne copie pas le champ SQL_DESC_ALLOC_TYPE, car le type d’allocation d’un descripteur ne peut pas être modifié. Les champs copiés remplacent les champs existants.  
  
 Un ARD sur un descripteur d’instruction peut servir de APD sur un autre descripteur d’instruction. Cela permet à une application de copier des lignes entre des tables sans copier les données au niveau de l’application. Pour ce faire, un descripteur de ligne décrivant une ligne extraite d’une table est réutilisé comme descripteur de paramètre pour un paramètre dans une instruction INSERT. Le type d’informations de SQL_MAX_CONCURRENT_ACTIVITIES doit être supérieur à 1 pour que cette opération aboutisse.
