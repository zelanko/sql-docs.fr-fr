---
title: Effet des transactions sur les curseurs et les instructions préparées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 83b693922d08f7298d0c5282fe2c7d1c20149d5b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046883"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Effet des transactions sur les curseurs et les instructions préparées
La validation ou la restauration d’une transaction a les effets suivants sur les curseurs et les plans d’accès :  
  
-   Tous les curseurs sont fermés, et les plans d’accès pour les instructions préparées sur cette connexion sont supprimés.  
  
-   Tous les curseurs sont fermés, et les plans d’accès pour les instructions préparées sur cette connexion restent intacts.  
  
-   Tous les curseurs restent ouverts et les plans d’accès pour les instructions préparées sur cette connexion restent intacts.  
  
 Par exemple, supposons qu’une source de données présente le premier comportement de cette liste, ce qui est le plus restrictif de ces comportements. Supposons à présent qu’une application effectue les opérations suivantes :  
  
1.  Définit le mode de validation sur Manual-commit.  
  
2.  Crée un jeu de résultats de commandes client sur l’instruction 1.  
  
3.  Crée un jeu de résultats de lignes dans une commande client sur l’instruction 2, lorsque l’utilisateur met en surbrillance cette commande.  
  
4.  Appelle **SQLExecute** pour exécuter une instruction Update positionnée qui a été préparée sur l’instruction 3, lorsque l’utilisateur met à jour une ligne.  
  
5.  Appelle **SQLEndTran** pour valider l’instruction de mise à jour positionnée.  
  
 En raison du comportement de la source de données, l’appel à **SQLEndTran** à l’étape 5 provoque la fermeture des curseurs sur les instructions 1 et 2 et la suppression du plan d’accès sur toutes les instructions. L’application doit réexécuter les instructions 1 et 2 pour recréer les jeux de résultats et repréparer l’instruction sur l’instruction 3.  
  
 En mode de validation automatique, les fonctions autres que **SQLEndTran** valident les transactions :  
  
-   **SQLExecute** ou **SQLExecDirect** dans l’exemple précédent, l’appel à **SQLExecute** à l’étape 4 valide une transaction. Ainsi, la source de données ferme les curseurs sur les instructions 1 et 2 et supprime le plan d’accès sur toutes les instructions de cette connexion.  
  
-   **SQLBulkOperations** ou **SQLSetPos** dans l’exemple précédent, supposons que à l’étape 4 l’application appelle **SQLSetPos** avec l’option SQL_UPDATE sur l’instruction 2, au lieu d’exécuter une instruction Update positionnée sur l’instruction 3. Cela a pour effet de valider une transaction et de faire en sorte que la source de données ferme les curseurs sur les instructions 1 et 2, et ignore tous les plans d’accès sur cette connexion.  
  
-   **SQLCloseCursor** Dans l’exemple précédent, supposons que lorsque l’utilisateur met en surbrillance une commande différente, l’application appelle **SQLCloseCursor** sur l’instruction 2 avant de créer un résultat des lignes pour la nouvelle commande client. L’appel à **SQLCloseCursor** valide l’instruction **Select** qui a créé le jeu de résultats de lignes et fait en sorte que la source de données ferme le curseur sur l’instruction 1, puis ignore tous les plans d’accès sur cette connexion.  
  
 Applications, en particulier les applications à écran dans lesquelles l’utilisateur fait défiler le jeu de résultats et met à jour ou supprime des lignes, doit veiller à contourner ce comportement.  
  
 Pour déterminer le comportement d’une source de données lorsqu’une transaction est validée ou restaurée, une application appelle **SQLGetInfo** avec les options SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR.
