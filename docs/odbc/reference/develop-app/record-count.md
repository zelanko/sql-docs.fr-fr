---
title: Nombre record de disques Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28e503ae4602d87fc9138ed018ee1e95f135ec57
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281815"
---
# <a name="record-count"></a>Nombre d'enregistrements
Le champ d’en-tête SQL_DESC_COUNT d’un descripteur est l’indice à un seul niveau de l’enregistrement le plus numéroté qui contient des données. Ce champ n’est pas un compte de toutes les colonnes ou paramètres qui sont liés. Lorsqu’un descripteur est attribué, la valeur initiale de SQL_DESC_COUNT est de 0.  
  
 Le conducteur prend toutes les mesures nécessaires pour allouer et maintenir tout stockage dont il a besoin pour conserver les informations descripteur. L’application ne précise pas explicitement la taille d’un descripteur ni n’alloue de nouveaux enregistrements. Lorsque l’application fournit des informations pour un dossier descripteur dont le nombre est supérieur à la valeur de SQL_DESC_COUNT, le conducteur augmente automatiquement SQL_DESC_COUNT. Lorsque l’application débinde le dossier descripteur le plus numéroté, le conducteur diminue automatiquement SQL_DESC_COUNT pour contenir le nombre du record le plus élevé restant.
