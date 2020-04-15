---
title: Effet des transactions sur les curseurs et les déclarations préparées .fr Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef3cb4095410b8ccb03b0a138f65b8df2cfb1a4b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300469"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Effet des transactions sur les curseurs et les instructions préparées
L’engagement ou le recul d’une transaction a l’effet suivant sur les curseurs et les plans d’accès :  
  
-   Tous les curseurs sont fermés, et les plans d’accès pour les instructions préparées sur cette connexion sont supprimés.  
  
-   Tous les curseurs sont fermés, et les plans d’accès pour les déclarations préparées sur cette connexion restent intacts.  
  
-   Tous les curseurs restent ouverts, et les plans d’accès pour les déclarations préparées sur cette connexion restent intacts.  
  
 Par exemple, supposons qu’une source de données présente le premier comportement de cette liste, le plus restrictif de ces comportements. Supposons maintenant qu’une demande fasse ce qui suit :  
  
1.  Définit le mode de validation pour s’engager manuellement.  
  
2.  Crée un ensemble de résultats de commandes sur l’instruction 1.  
  
3.  Crée un ensemble de résultats des lignes dans un ordre de vente sur l’instruction 2, lorsque l’utilisateur met en évidence cette commande.  
  
4.  Appelle **SQLExecute** pour exécuter une mise à jour positionnée qui a été préparée sur l’instruction 3, lorsque l’utilisateur met à jour une ligne.  
  
5.  Appelle **SQLEndTran** pour valider la mise à jour positionnée.  
  
 En raison du comportement de la source de données, l’appel à **SQLEndTran** à l’étape 5 l’amène à fermer les curseurs sur les instructions 1 et 2 et à supprimer le plan d’accès sur toutes les déclarations. La demande doit réexaminer les déclarations 1 et 2 pour recréer les ensembles de résultats et refonder l’énoncé sur la déclaration 3.  
  
 En mode auto-commit, les fonctions autres que **SQLEndTran** commit transactions:  
  
-   **SQLExecute** ou **SQLExecDirect** Dans l’exemple précédent, l’appel à **SQLExecute** à l’étape 4 engage une transaction. Cela provoque la source de données de fermer les curseurs sur les déclarations 1 et 2 et de supprimer le plan d’accès sur toutes les déclarations sur cette connexion.  
  
-   **SQLBulkOperations** ou **SQLSetPos** Dans l’exemple précédent, supposons que dans l’étape 4 de la demande appelle **SQLSetPos** avec l’option SQL_UPDATE sur la déclaration 2, au lieu d’exécuter une déclaration de mise à jour positionnée sur la déclaration 3. Cela engage une transaction et provoque la source de données de fermer les curseurs sur les déclarations 1 et 2, et rejette tous les plans d’accès sur cette connexion.  
  
-   **SQLCloseCursor** Dans l’exemple précédent, supposons que lorsque l’utilisateur met en évidence un ordre de vente différent, l’application appelle **SQLCloseCursor** sur la déclaration 2 avant de créer un résultat des lignes pour le nouvel ordre de vente. L’appel à **SQLCloseCursor** engage la déclaration **SELECT** qui a créé l’ensemble de lignes de résultat et provoque la source de données de fermer le curseur sur l’instruction 1, puis rejette tous les plans d’accès sur cette connexion.  
  
 Les applications, en particulier les applications basées sur l’écran dans lesquelles l’utilisateur fait défiler autour de l’ensemble de résultats et met à jour ou supprime les lignes, doivent faire attention au code autour de ce comportement.  
  
 Pour déterminer comment une source de données se comporte lorsqu’une transaction est engagée ou annulée, une application appelle **SQLGetInfo** avec les options SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR.
