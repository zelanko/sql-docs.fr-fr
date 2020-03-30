---
title: Gérer les erreurs | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6277b3ecf0160078fa47bc79994d31f64519d9b7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028028"
---
# <a name="handling-errors"></a>Gestion des erreurs
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], toutes les erreurs de base de données sont retournées à votre application Java en tant qu’exceptions à l’aide de la classe [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Les méthodes suivantes de la classe SQLServerException sont héritées de java.sql.SQLException et de java.lang.Throwable, et elles peuvent être utilisées pour retourner des informations spécifiques sur l’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’est produite :  
  
-   `getSQLState()` retourne l'état de code standard X/Open ou SQL99 de l'exception.
  
-   `getErrorCode()` retourne le numéro d'erreur de base de données spécifique.
  
-   `getMessage()` retourne le texte intégral de l'exception. Le texte du message d'erreur décrit le problème et inclut souvent des espaces réservés pour des informations, tels que des noms d'objets insérés dans le message d'erreur lors de son affichage.
  
-   `getNextException()` retourne l'objet `SQLServerException` suivant ou la valeur « null » s'il n'y a pas d'objet d'exception à retourner.

-   `getSQLServerError()` retourne l’objet `SQLServerError` contenant des informations détaillées sur l’exception envoyée par SQL Server. Cette méthode retourne la valeur Null si aucune erreur de serveur ne s’est produite.

Les méthodes suivantes de la classe `SQLServerError` permettent d’obtenir des détails supplémentaires sur l’erreur générée à partir du serveur.

-   `SQLServerError.getErrorMessage()` retourne le message d’erreur envoyé par le serveur.

-   `SQLServerError.getErrorNumber()` retourne un nombre identifiant le type de l’erreur.

-   `SQLServerError.getErrorState()` retourne un code d’erreur numérique de SQL Server qui représente une erreur, un avertissement ou un message « Aucune donnée trouvée ».

-   `SQLServerError.getErrorSeverity()` retourne le niveau de gravité de l’erreur reçue.

-   `SQLServerError.getServerName()` retourne le nom de l’ordinateur exécutant une instance de SQL Server qui a généré l’erreur.

-   `SQLServerError.getProcedureName()` retourne le nom de la procédure stockée ou de l’appel de procédure distante (RPC) qui a généré l’erreur.

-   `SQLServerError.getLineNumber()` retourne le numéro de la ligne au sein du lot de commandes Transact-SQL ou de la procédure stockée qui a généré l’erreur.
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est passée à la fonction et une instruction SQL incorrecte est créée, qui ne contient pas de clause FROM. Ensuite, l'instruction est exécutée et une exception SQL est traitée.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic de problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
