---
title: Effet des Transactions sur les curseurs et les instructions préparées | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 41c2c6b06744965144ca9d5feb27e9ea16d9903c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802027"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>Effet des transactions sur les curseurs et les instructions préparées
Validation ou la restauration d’une transaction a l’effet suivant sur les curseurs et les plans d’accès :  
  
-   Tous les curseurs sont fermés, et les plans d’accès pour les instructions préparées sur cette connexion sont supprimés.  
  
-   Tous les curseurs sont fermés, et les plans d’accès pour les instructions préparées sur cette connexion restent intactes.  
  
-   Tous les curseurs restent ouverts et les plans d’accès pour les instructions préparées sur cette connexion restent intacts.  
  
 Par exemple, qu'une source de données présente le comportement de premier dans cette liste, la plus restrictive de ces comportements. Maintenant Supposons qu’une application effectue les opérations suivantes :  
  
1.  Définit le mode de validation pour la validation manuelle.  
  
2.  Crée un jeu de résultats des commandes client sur l’instruction 1.  
  
3.  Crée un jeu de résultats des lignes dans une commande client sur l’instruction 2, lorsque l’utilisateur met en surbrillance cet ordre.  
  
4.  Appels **SQLExecute** pour exécuter une instruction de mise à jour positionnée qui a été préparée sur l’instruction 3, lorsque l’utilisateur met à jour une ligne.  
  
5.  Appels **SQLEndTran** pour valider l’instruction de mise à jour positionnée.  
  
 En raison du comportement de la source de données, l’appel à **SQLEndTran** à l’étape 5 oblige ce dernier à fermer les curseurs sur les instructions 1 et 2 et de suppression du plan d’accès sur toutes les instructions. L’application doit redéfinir les jeux d’instructions 1 et 2 pour recréer le résultat et reprepare l’instruction sur l’instruction 3.  
  
 En mode de validation automatique, fonctions autres que **SQLEndTran** valider des transactions :  
  
-   **SQLExecute** ou **SQLExecDirect** dans l’exemple précédent, l’appel à **SQLExecute** à l’étape 4 valide une transaction. Cela entraîne la source de données fermer les curseurs sur les instructions 1 et 2 et de supprimer le plan d’accès sur toutes les instructions sur cette connexion.  
  
-   **SQLBulkOperations** ou **SQLSetPos** dans l’exemple précédent, supposons qu’à l’étape 4 l’application appelle **SQLSetPos** avec l’option SQL_UPDATE sur instruction 2, au lieu d’exécuter un instruction de mise à jour positionnée sur instruction 3. Cela valide une transaction et provoque la source de données fermer les curseurs sur les instructions 1 et 2 et ignore tous les plans d’accès sur cette connexion.  
  
-   **SQLCloseCursor** dans l’exemple précédent, supposons que lorsque l’utilisateur met en évidence une autre commande, l’application appelle **SQLCloseCursor** sur instruction 2 avant de créer un résultat des lignes pour les nouvelles ventes ordre. L’appel à **SQLCloseCursor** valide le **sélectionnez** instruction qui a créé le jeu de résultats de lignes et provoque la source de données fermer le curseur sur l’instruction 1 et ignore ensuite tous les plans d’accès sur ce connexion.  
  
 Les applications, en particulier sur un écran dans lequel l’utilisateur fait défiler autour de l’ensemble de résultats et les mises à jour ou supprime des lignes, doivent être prudent coder autour de ce comportement.  
  
 Pour déterminer le comporte d’une source de données lorsqu’une transaction est validée ou restaurée, une application appelle **SQLGetInfo** avec les options SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR.
