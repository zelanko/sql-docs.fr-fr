---
title: Copier les descripteurs Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301668"
---
# <a name="copying-descriptors"></a>Copie de descripteurs
La fonction **SQLCopyDesc** est appelée à copier les champs d’un descripteur à un autre descripteur. Les champs ne peuvent être copiés qu’à un descripteur d’application ou à un IPD, mais pas à un IRD. Les champs peuvent être copiés à partir de n’importe quel type de descripteur. Seuls les champs définis pour la source et les descripteurs cibles sont copiés. **SQLCopyDesc** ne copie pas le champ SQL_DESC_ALLOC_TYPE, parce que le type d’allocation d’un descripteur ne peut pas être modifié. Les champs copiés surmorment les champs existants.  
  
 Une ARD sur une poignée de déclaration peut servir d’APD sur une autre poignée de déclaration. Cela permet à une application de copier des lignes entre les tables sans copier les données au niveau de l’application. Pour ce faire, un descripteur de ligne qui décrit une rangée récupérée d’une table est réutilisé comme un descripteur de paramètres pour un paramètre dans une déclaration INSERT. Le type d’information SQL_MAX_CONCURRENT_ACTIVITIES doit être supérieur à 1 pour que cette opération réussisse.
