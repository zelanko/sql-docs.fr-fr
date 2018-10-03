---
title: Rôle du pilote | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2687e1a68789566fd7b660a8241d65ff4714a933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633567"
---
# <a name="role-of-the-driver"></a>Rôle du pilote
Le pilote vérifie toutes les erreurs et avertissements ne pas vérifiées par le Gestionnaire de pilotes et trie les enregistrements d’état qu’il génère. (Une application ODBC 2. *x* pilote ne trie pas les enregistrements d’état.) Cela inclut les erreurs et avertissements de troncation de données, conversion de données, la syntaxe et des transitions d’état. Le pilote peut également contrôler les erreurs et avertissements partiellement activés par le Gestionnaire de pilotes. Par exemple, bien que le Gestionnaire de pilotes vérifie si la valeur de *opération* dans **SQLSetPos** est autorisé, le pilote doit vérifier si elle est prise en charge.  
  
 Le pilote mappe également *erreurs natives* , autrement dit, les erreurs retournées par la source de données — à SQLSTATE. Par exemple, le pilote peut mapper un nombre d’erreurs natives différentes pour le syntaxe SQL non conforme à SQLSTATE 42000 (syntaxe ou violation d’accès). Le pilote retourne le numéro d’erreur natif dans le champ SQL_DIAG_NATIVE de l’enregistrement de l’état. Documentation du pilote doit indiquer la façon dont des erreurs et avertissements sont mappés à partir de la source de données aux arguments dans **SQLGetDiagRec** et **SQLGetDiagField**.
