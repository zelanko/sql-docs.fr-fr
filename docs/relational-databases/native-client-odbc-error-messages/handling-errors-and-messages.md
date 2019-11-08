---
title: Gestion des erreurs et des messages | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 779a06881d49cf7853f20a5241c52b25d4ccfc24
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783467"
---
# <a name="handling-errors-and-messages"></a>Gestion des erreurs et des messages
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lorsqu'une application appelle une fonction ODBC, le pilote exécute la fonction et retourne les informations de diagnostic de deux façons : un code de retour indique le succès ou l'échec total d'une fonction ODBC et les enregistrements de diagnostic fournissent des informations détaillées sur la fonction. Les enregistrements de diagnostic comportent un enregistrement d'en-tête et des enregistrements d'état. Au moins un enregistrement de diagnostic, l'enregistrement d'en-tête, est retourné même si la fonction réussit.  
  
 Les informations de diagnostic sont utilisées au moment du développement pour intercepter les erreurs de programmation, telles que les handles non valides et les erreurs de syntaxe dans les instructions SQL codées de manière irréversible. Elles sont également utilisées au moment de l'exécution pour intercepter les avertissements et les erreurs d'exécution, tels que la troncation de données, les violations de règle et les erreurs de syntaxe des instructions SQL saisies par l'utilisateur. La logique du programme repose en général sur des codes de retour.  
  
 Par exemple, après qu’une application a appelé **SQLFetch** pour extraire les lignes d’un jeu de résultats, le code de retour indique si la fin du jeu de résultats a été atteinte (SQL_NO_DATA), si des messages d’information ont été retournés (SQL_SUCCESS_WITH_INFO) ou si un une erreur s’est produite (SQL_ERROR).  
  
 Si le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client retourne une valeur autre que SQL_SUCCESS, l’application peut appeler **SQLGetDiagRec** pour récupérer les messages d’information ou d’erreur. Utilisez **SQLGetDiagRec** pour faire défiler vers le haut et vers le haut l’ensemble de messages s’il y a plusieurs messages.  
  
 Le code de retour SQL_INVALID_HANDLE indique toujours une erreur de programmation et ne doit jamais se rencontrer au moment de l'exécution. Tous les autres codes de retour fournissent des informations d'exécution, bien que SQL_ERROR puisse indiquer une erreur de programmation.  
  
 La [!INCLUDE[msCoName](../../includes/msconame-md.md)] d’origine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] API native de DB-Library pour C permet à une application d’installer des fonctions de gestion des erreurs de rappel et de gestion des messages qui retournent des erreurs ou des messages. Certaines instructions [!INCLUDE[tsql](../../includes/tsql-md.md)], telles que PRINT, RAISERROR, DBCC et SET, retournent leurs résultats à la fonction gestionnaire des messages de DB-Library et non dans un jeu de résultats. Toutefois, l'API ODBC n'a aucune fonction de rappel similaire. Lorsque le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client détecte des messages provenant de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il définit le code de retour ODBC sur SQL_SUCCESS_WITH_INFO ou SQL_ERROR et retourne le message sous la forme d’un ou de plusieurs enregistrements de diagnostic. Par conséquent, une application ODBC doit tester avec soin ces codes de retour et appeler **SQLGetDiagRec** pour extraire les données de message.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [Suivi de l’accès aux données](https://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations apportées au suivi des erreurs ajoutées dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], consultez [accès aux informations de diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Traitement des instructions qui génèrent des messages](../../relational-databases/native-client-odbc-error-messages/processing-statements-that-generate-messages.md)  
  
-   [Enregistrements et champs de diagnostic](../../relational-databases/native-client-odbc-error-messages/diagnostic-records-and-fields.md)  
  
-   [Numéros des erreurs natives](../../relational-databases/native-client-odbc-error-messages/native-error-numbers.md)  
  
-   [Codes &#40;d’erreur SQLSTATE ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)  
  
-   [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
