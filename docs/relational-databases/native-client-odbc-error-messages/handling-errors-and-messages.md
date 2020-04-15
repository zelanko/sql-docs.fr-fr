---
title: Manipulation des erreurs et des messages Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59bb40dbfc7f8596968d2dc441396dc9c076bb82
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291659"
---
# <a name="handling-errors-and-messages"></a>Gestion des erreurs et des messages
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lorsqu'une application appelle une fonction ODBC, le pilote exécute la fonction et retourne les informations de diagnostic de deux façons : un code de retour indique le succès ou l'échec total d'une fonction ODBC et les enregistrements de diagnostic fournissent des informations détaillées sur la fonction. Les enregistrements de diagnostic comportent un enregistrement d'en-tête et des enregistrements d'état. Au moins un enregistrement de diagnostic, l'enregistrement d'en-tête, est retourné même si la fonction réussit.  
  
 Les informations de diagnostic sont utilisées au moment du développement pour intercepter les erreurs de programmation, telles que les handles non valides et les erreurs de syntaxe dans les instructions SQL codées de manière irréversible. Elles sont également utilisées au moment de l'exécution pour intercepter les avertissements et les erreurs d'exécution, tels que la troncation de données, les violations de règle et les erreurs de syntaxe des instructions SQL saisies par l'utilisateur. La logique du programme repose en général sur des codes de retour.  
  
 Par exemple, après qu’une application a appelé **SQLFetch** pour récupérer les lignes dans un ensemble de résultats, le code de retour indique si la fin de l’ensemble de résultat a été atteinte (SQL_NO_DATA), si des messages d’information ont été retournés (SQL_SUCCESS_WITH_INFO), ou si une erreur s’est produite (SQL_ERROR).  
  
 Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le conducteur de Native Client ODBC renvoie autre chose que SQL_SUCCESS, l’application peut appeler **SQLGetDiagRec** pour récupérer tout message d’information ou d’erreur. Utilisez **SQLGetDiagRec** pour faire défiler l’ensemble de messages s’il y a plus d’un message.  
  
 Le code de retour SQL_INVALID_HANDLE indique toujours une erreur de programmation et ne doit jamais se rencontrer au moment de l'exécution. Tous les autres codes de retour fournissent des informations d'exécution, bien que SQL_ERROR puisse indiquer une erreur de programmation.  
  
 L’API d’origine, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB-Library for C, permet à une application d’installer des fonctions de traitement des erreurs et de traitement des messages qui renvoient des erreurs ou des messages. Certaines instructions [!INCLUDE[tsql](../../includes/tsql-md.md)], telles que PRINT, RAISERROR, DBCC et SET, retournent leurs résultats à la fonction gestionnaire des messages de DB-Library et non dans un jeu de résultats. Toutefois, l'API ODBC n'a aucune fonction de rappel similaire. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le conducteur de Native Client ODBC détecte les messages qui reviennent, il définit le code de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]retour ODBC à SQL_SUCCESS_WITH_INFO ou SQL_ERROR et renvoie le message comme un ou plusieurs dossiers diagnostiques. Par conséquent, une application ODBC doit tester soigneusement ces codes de retour et appeler **SQLGetDiagRec** pour récupérer les données de messages.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [Suivi de l’accès aux données](https://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations du suivi des erreurs ajoutées dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], consultez [Accès aux informations de diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Traitement des instructions qui génèrent des messages](../../relational-databases/native-client-odbc-error-messages/processing-statements-that-generate-messages.md)  
  
-   [Enregistrements et champs de diagnostic](../../relational-databases/native-client-odbc-error-messages/diagnostic-records-and-fields.md)  
  
-   [Numéros des erreurs natives](../../relational-databases/native-client-odbc-error-messages/native-error-numbers.md)  
  
-   [SQLSTATE &#40;codes d’erreur ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)  
  
-   [Messages d'erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
