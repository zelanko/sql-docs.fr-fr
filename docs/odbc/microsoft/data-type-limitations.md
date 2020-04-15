---
title: Limitations de type de données (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4beaf91a4ead743e3e8a2e32578796baba3c17be
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280669"
---
# <a name="data-type-limitations"></a>Limitations des types de données
Les pilotes microsoft ODBC Desktop Database imposent les limites suivantes sur les types de données :  
  
|Type de données|Description|  
|---------------|-----------------|  
|Tous les types de données|Les défaillances de conversion de type peuvent entraîner l’ensemble de la colonne affectée à NULL.|  
|BINARY|La création d’une colonne BINAIRE de longueur zéro renvoie en fait une colonne BINAIRE de 255 byte.|  
|DATE|Le type de données DATE ne peut pas être converti en un autre type de données (ou lui-même) par la fonction CONVERT.|  
|DECIMAL (Exact Numeric)|Non pris en charge.|  
|Types de données à point flottant|Le nombre de décimales dans un numéro de point flottant peut être limité par le format de nombre défini dans la section internationale du panneau de contrôle Windows.|  
|NUMERIC|Prend en charge une précision maximale et une échelle de 28.|  
|timestamp|Le type de données TIMESTAMP ne peut pas être converti en lui-même par la fonction CONVERT.|  
|TINYINT|Les valeurs TINYINT ne sont toujours pas signées.|  
|Cordes zéro longueur|Lorsqu’un dBASE, Microsoft Excel, Paradox ou Textdriver est utilisé, l’insertion d’une chaîne de longueur zéro dans une colonne insère en fait un NULL à la place.|
