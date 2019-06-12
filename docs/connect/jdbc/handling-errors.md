---
title: Gestion des erreurs | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a69bf1d98d666b0b4b76be604abc31e28958adb4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781701"
---
# <a name="handling-errors"></a>Gestion des erreurs
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], toutes les erreurs de base de données sont retournées à votre application Java en tant qu’exceptions à l’aide de la classe [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Les méthodes suivantes de la classe SQLServerException sont héritées de java.sql.SQLException et de java.lang.Throwable, et elles peuvent être utilisées pour retourner des informations spécifiques sur l’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’est produite :  
  
-   `getSQLState()` retourne l'état de code standard X/Open ou SQL99 de l'exception.
  
-   `getErrorCode()` retourne le numéro d'erreur de base de données spécifique.
  
-   `getMessage()` retourne le texte intégral de l'exception. Le texte du message d'erreur décrit le problème et inclut souvent des espaces réservés pour des informations, tels que des noms d'objets insérés dans le message d'erreur lors de son affichage.
  
-   `getNextException()` retourne l'objet `SQLServerException` suivant ou la valeur « null » s'il n'y a pas d'objet d'exception à retourner.

-   `getSQLServerError()` Retourne le `SQLServerError` objet contenant des informations détaillées sur l’exception comme reçu à partir de SQL Server. Cette méthode retourne la valeur null si aucune erreur de serveur se n’est produite.

Les méthodes suivantes de la `SQLServerError` classe peut être utilisée pour obtenir des détails supplémentaires sur l’erreur générée à partir du serveur.

-   `SQLServerError.getErrorMessage()` Retourne le message d’erreur comme reçu à partir du serveur.

-   `SQLServerError.getErrorNumber()` Retourne un nombre qui identifie le type de l’erreur.

-   `SQLServerError.getErrorState()` Retourne un code d’erreur numérique à partir de SQL Server qui représente un message d’erreur, avertissement ou « aucune donnée trouvée ».

-   `SQLServerError.getErrorSeverity()` Retourne le niveau de gravité de l’erreur reçue.

-   `SQLServerError.getServerName()` Retourne le nom de l’ordinateur qui exécute une instance de SQL Server qui a généré l’erreur.

-   `SQLServerError.getProcedureName()` Retourne le nom de la procédure stockée ou d’un appel de procédure distante (RPC) qui a généré l’erreur.

-   `SQLServerError.getLineNumber()` Retourne le numéro de ligne dans le lot de commandes Transact-SQL ou une procédure stockée qui a généré l’erreur.
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est passée à la fonction et une instruction SQL incorrecte est créée, qui ne contient pas de clause FROM. Ensuite, l'instruction est exécutée et une exception SQL est traitée.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic des problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
