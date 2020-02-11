---
title: Exécution préparée ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2107ca1eeecc6fad24311c5bce629784ae4ceff0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023280"
---
# <a name="prepared-execution-odbc"></a>Exécution préparée dans ODBC
L’exécution préparée est un moyen efficace d’exécuter une instruction plusieurs fois. L’instruction est tout d’abord compilée, ou *préparée,* dans un plan d’accès. Le plan d’accès est ensuite exécuté une ou plusieurs fois ultérieurement. Pour plus d’informations sur les plans d’accès, consultez [traitement d’une instruction SQL](../../../odbc/reference/processing-a-sql-statement.md).  
  
 L’exécution préparée est couramment utilisée par les applications verticales et personnalisées pour exécuter de manière répétée la même instruction SQL paramétrée. Par exemple, le code suivant prépare une instruction pour mettre à jour les prix de différentes parties. Il exécute ensuite l’instruction plusieurs fois avec des valeurs de paramètre différentes à chaque fois.  
  
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
  
 L’exécution préparée est plus rapide que l’exécution directe pour les instructions exécutées plusieurs fois, principalement parce que l’instruction n’est compilée qu’une seule fois ; les instructions exécutées directement sont compilées chaque fois qu’elles sont exécutées. L’exécution préparée peut également permettre de réduire le trafic réseau car le pilote peut envoyer un identificateur de plan d’accès à la source de données chaque fois que l’instruction est exécutée, plutôt qu’une instruction SQL entière, si la source de données prend en charge les identificateurs de plan d’accès.  
  
 L’application peut récupérer les métadonnées du jeu de résultats après la préparation de l’instruction et avant son exécution. Toutefois, le retour de métadonnées pour les instructions préparées et non exécutées est onéreux pour certains pilotes et doit être évité par les applications interopérables si possible. Pour plus d’informations, consultez [métadonnées du jeu de résultats](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 L'exécution préparée ne doit pas être utilisée pour les instructions exécutées une seule fois. Pour ces instructions, elle est légèrement plus lente que l’exécution directe, car elle nécessite un appel de fonction ODBC supplémentaire.  
  
> [!IMPORTANT]  
>  La validation ou la restauration d’une transaction, en appelant explicitement **SQLEndTran** ou en mode de validation automatique, fait que certaines sources de données suppriment les plans d’accès pour toutes les instructions sur une connexion. Pour plus d’informations, consultez les options SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .  
  
 Pour préparer et exécuter une instruction, l’application :  
  
1.  Appelle **SQLPrepare** et lui transmet une chaîne contenant l’instruction SQL.  
  
2.  Définit les valeurs de tous les paramètres. Les paramètres peuvent être définis avant ou après la préparation de l’instruction. Pour plus d’informations, consultez [paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
3.  Appelle **SQLExecute** et effectue tout traitement supplémentaire nécessaire, tel que l’extraction de données.  
  
4.  Répète les étapes 2 et 3, si nécessaire.  
  
5.  Lorsque **SQLPrepare** est appelé, le pilote :  
  
    -   Modifie l’instruction SQL pour utiliser la grammaire SQL de la source de données sans analyser l’instruction. Cela comprend le remplacement des séquences d’échappement présentées dans [séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L’application peut récupérer la forme modifiée d’une instruction SQL en appelant **SQLNativeSql**. Les séquences d’échappement ne sont pas remplacées si l’attribut d’instruction SQL_ATTR_NOSCAN est défini.  
  
    -   Envoie l’instruction à la source de données pour la préparation.  
  
    -   Stocke l’identificateur de plan d’accès retourné pour une exécution ultérieure (si la préparation a réussi) ou retourne des erreurs (en cas d’échec de la préparation). Les erreurs incluent des erreurs syntaxiques telles que SQLSTATE 42000 (erreur de syntaxe ou violation d’accès) et des erreurs sémantiques telles que SQLSTATE 42S02 (table de base ou vue introuvable).  
  
        > [!NOTE]  
        >  Certains pilotes ne retournent pas d’erreurs à ce stade, mais les retournent à la place lorsque l’instruction est exécutée ou lorsque les fonctions de catalogue sont appelées. Par conséquent, **SQLPrepare** peut sembler avoir réussi en fait qu’il a échoué.  
  
6.  Lorsque **SQLExecute** est appelé, le pilote :  
  
    -   Récupère les valeurs de paramètres actuelles et les convertit si nécessaire. Pour plus d’informations, consultez [paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
    -   Envoie l’identificateur de plan d’accès et les valeurs de paramètre converties à la source de données.  
  
    -   Retourne les erreurs éventuelles. Il s’agit généralement d’erreurs d’exécution, telles que SQLSTATE 24000 (état de curseur non valide). Toutefois, certains pilotes retournent des erreurs syntaxiques et sémantiques à ce stade.  
  
 Si la source de données ne prend pas en charge la préparation des instructions, le pilote doit l’émuler dans la mesure du possible. Par exemple, le pilote peut ne rien faire lorsque **SQLPrepare** est appelé, puis effectuer une exécution directe de l’instruction lorsque **SQLExecute** est appelé.  
  
 Si la source de données prend en charge la vérification de la syntaxe sans exécution, le pilote peut soumettre l’instruction de vérification lorsque **SQLPrepare** est appelé et soumettre l’instruction pour exécution lorsque **SQLExecute** est appelé.  
  
 Si le pilote ne peut pas émuler la préparation des instructions, il stocke l’instruction quand **SQLPrepare** est appelé et l’envoie pour exécution lorsque **SQLExecute** est appelé.  
  
 Étant donné que la préparation des instructions émulées n’est pas parfaite, **SQLExecute** peut retourner toutes les erreurs normalement retournées par **SQLPrepare**.
