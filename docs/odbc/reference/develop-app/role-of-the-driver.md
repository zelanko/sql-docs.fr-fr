---
title: Rôle du conducteur (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c683d990aaa3fd6892369e734c06fd1c356bd0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304280"
---
# <a name="role-of-the-driver"></a>Rôle du pilote
Le conducteur vérifie toutes les erreurs et avertissements non vérifiés par le gestionnaire de pilote et les registres d’état qu’il génère. (Un ODBC 2. *x* le conducteur ne commande pas d’enregistrements d’état.) Cela comprend les erreurs et les avertissements dans la troncation de données, la conversion des données, la syntaxe et certaines transitions d’état. Le conducteur peut également vérifier les erreurs et les avertissements partiellement vérifiés par le gestionnaire de pilote. Par exemple, bien que le gestionnaire de conducteur vérifie si la valeur de *l’opération* dans **SQLSetPos** est légale, le conducteur doit vérifier si elle est prise en charge.  
  
 Le conducteur cartographie également les *erreurs indigènes* - c’est-à-dire les erreurs retournées par la source de données - aux SQLSTATEs. Par exemple, le conducteur peut cartographier un certain nombre d’erreurs indigènes différentes pour la syntaxe SQL illégale à SQLSTATE 42000 (erreur syntaxe ou violation d’accès). Le conducteur retourne le numéro d’erreur natif dans le SQL_DIAG_NATIVE champ du dossier d’état. La documentation du conducteur devrait montrer comment les erreurs et les avertissements sont cartographiés à partir de la source de données aux arguments de **SQLGetDiagRec** et **SQLGetDiagField**.
