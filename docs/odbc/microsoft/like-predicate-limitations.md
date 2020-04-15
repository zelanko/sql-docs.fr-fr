---
title: LIKE Predicate Limitations (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d596d688956d7bdbf3d9125184d81c16249781c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298959"
---
# <a name="like-predicate-limitations"></a>LIKE, prédicat - limitations
Si les données d’une colonne sont supérieures à 255 caractères, la comparaison LIKE ne sera basée que sur les 255 premiers caractères.  
  
 Un LIKE utilisé dans une procédure n’est pris en charge qu’avec des motifs constants. Les pilotes de base de données de bureau prennent en charge l’appariement des modèles SQL-92 LIKE.  
  
 L’utilisation d’une clause d’évasion dans un prédicat LIKE n’est pas étayée.  
  
 Une comparaison LIKE ne doit pas être effectuée sur une colonne contenant des données d’un type de données numériques ou flottantes. Les résultats peuvent être imprévisibles. Pour plus d’informations, consultez le *Guide du programmeur de moteurs microsoft Jet Database Engine*.
