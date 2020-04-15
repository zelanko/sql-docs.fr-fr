---
title: Exécution préparée ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prepared execution [ODBC]
- SQL statements [ODBC], prepared execution
- SQL statements [ODBC], executing
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 147ca85b21296575ff55afbe66ab286cc4824fae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282309"
---
# <a name="prepared-execution-odbc"></a>Exécution préparée dans ODBC
L’exécution préparée est un moyen efficace d’exécuter une déclaration plus d’une fois. L’énoncé est d’abord compilé ou *préparé* dans un plan d’accès. Le plan d’accès est ensuite exécuté une ou plusieurs fois plus tard. Pour plus d’informations sur les plans d’accès, voir [Traitement d’un communiqué SQL](../../../odbc/reference/processing-a-sql-statement.md).  
  
 L’exécution préparée est couramment utilisée par les applications verticales et personnalisées pour exécuter à plusieurs reprises la même déclaration SQL paramétrée. Par exemple, le code suivant prépare une déclaration pour mettre à jour les prix des différentes pièces. Il exécute ensuite l’instruction plusieurs fois avec des valeurs de paramètres différentes à chaque fois.  
  
```  
SQLREAL       Price;  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0, PriceInd = 0;  
  
// Prepare a statement to update salaries in the Employees table.  
SQLPrepare(hstmt, "UPDATE Parts SET Price = ? WHERE PartID = ?", SQL_NTS);  
  
// Bind Price to the parameter for the Price column and PartID to  
// the parameter for the PartID column.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &PartID, 0, &PartIDInd);  
  
// Repeatedly execute the statement.  
while (GetPrice(&PartID, &Price)) {  
   SQLExecute(hstmt);  
}  
```  
  
 L’exécution préparée est plus rapide que l’exécution directe pour les déclarations exécutées plus d’une fois, principalement parce que la déclaration n’est compilée qu’une seule fois; les déclarations exécutées directement sont compilées chaque fois qu’elles sont exécutées. L’exécution préparée peut également fournir une réduction du trafic réseau parce que le conducteur peut envoyer un identifiant de plan d’accès à la source de données chaque fois que l’instruction est exécutée, plutôt qu’une déclaration entière SQL, si la source de données prend en charge les identifiants de plan d’accès.  
  
 L’application peut récupérer les métadonnées pour le résultat défini après la préparation de l’instruction et avant qu’elle ne soit exécutée. Toutefois, le retour des métadonnées pour les relevés préparés et non exécutés coûte cher à certains conducteurs et doit être évité par des applications interopérables si possible. Pour plus d’informations, voir [Métadonnées Result Set](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 L'exécution préparée ne doit pas être utilisée pour les instructions exécutées une seule fois. Pour de telles déclarations, il est légèrement plus lent que l’exécution directe, car il nécessite un appel de fonction ODBC supplémentaire.  
  
> [!IMPORTANT]  
>  L’engagement ou le recul d’une transaction, soit en appelant explicitement **SQLEndTran,** soit en travaillant en mode auto-commit, oblige certaines sources de données à supprimer les plans d’accès pour toutes les déclarations sur une connexion. Pour plus d’informations, consultez les options de SQL_CURSOR_COMMIT_BEHAVIOR et de SQL_CURSOR_ROLLBACK_BEHAVIOR dans la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
 Pour préparer et exécuter une déclaration, l’application :  
  
1.  Appelle **SQLPrepare** et lui passe une chaîne contenant la déclaration SQL.  
  
2.  Définit les valeurs de tous les paramètres. Les paramètres peuvent effectivement être définis avant ou après la préparation de l’instruction. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.  
  
3.  Appelle **SQLExecute** et effectue tout traitement supplémentaire nécessaire, comme l’adage des données.  
  
4.  Répéte les étapes 2 et 3 au besoin.  
  
5.  Lorsque **SQLPrepare** est appelé, le conducteur:  
  
    -   Modifie la déclaration SQL pour utiliser la grammaire SQL de la source de données sans analyser la déclaration. Cela comprend le remplacement des séquences d’évacuation discutées dans [Escape Sequences dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L’application peut récupérer la forme modifiée d’une déclaration SQL en appelant **SQLNativeSql**. Les séquences d’évasion ne sont pas remplacées si l’attribut de l’SQL_ATTR_NOSCAN est défini.  
  
    -   Envoie l’instruction à la source de données pour la préparation.  
  
    -   Stocke l’identifiant de plan d’accès retourné pour une exécution ultérieure (si la préparation a réussi) ou renvoie toute erreur (si la préparation a échoué). Les erreurs comprennent des erreurs syntaxiques telles que SQLSTATE 42000 (erreur syntaxe ou violation d’accès) et des erreurs sémantiques telles que SQLSTATE 42S02 (tableau de base ou vue non trouvée).  
  
        > [!NOTE]  
        >  Certains pilotes ne retournent pas les erreurs à ce stade, mais les retournent plutôt lorsque l’instruction est exécutée ou lorsque les fonctions du catalogue sont appelées. Ainsi, **SQLPrepare** pourrait sembler avoir réussi alors qu’en fait il a échoué.  
  
6.  Lorsque **SQLExecute** est appelé, le conducteur:  
  
    -   Récupère les valeurs de paramètres actuelles et les convertit au besoin. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.  
  
    -   Envoie l’identifiant du plan d’accès et les valeurs de paramètres converties à la source de données.  
  
    -   Retourne toutes les erreurs. Il s’agit généralement d’erreurs de temps d’exécution comme SQLSTATE 24000 (État de curseur invalide). Cependant, certains conducteurs retournent des erreurs syntaxiques et sémantiques à ce stade.  
  
 Si la source de données ne prend pas en charge la préparation de l’instruction, le conducteur doit l’imiter dans la mesure du possible. Par exemple, le conducteur peut ne rien faire lorsque **SQLPrepare** est appelé, puis effectuer l’exécution directe de la déclaration lorsque **SQLExecute** est appelé.  
  
 Si la source de données prend en charge la vérification de la syntaxe sans exécution, le conducteur peut soumettre la déclaration pour vérifier quand **SQLPrepare** est appelé et soumettre la déclaration pour l’exécution lorsque **SQLExecute** est appelé.  
  
 Si le conducteur ne peut pas imiter la préparation de l’instruction, il stocke l’instruction lorsque **SQLPrepare** est appelé et le soumet pour exécution lorsque **SQLExecute** est appelé.  
  
 Parce que la préparation de déclaration imitée n’est pas parfaite, **SQLExecute** peut retourner toutes les erreurs normalement retournées par **SQLPrepare**.
