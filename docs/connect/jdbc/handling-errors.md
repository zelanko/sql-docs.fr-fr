---
title: Gestion des erreurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 066aa64a529d2066c0dcce50cd2f2aff12dcf948
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758987"
---
# <a name="handling-errors"></a>Gestion des erreurs
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], toutes les erreurs de base de données sont retournées à votre application Java en tant qu’exceptions à l’aide de la classe [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Les méthodes suivantes de la classe SQLServerException sont héritées de java.sql.SQLException et de java.lang.Throwable, et elles peuvent être utilisées pour retourner des informations spécifiques sur l’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’est produite :  
  
-   getSQLState retourne le code de l’état standard X/Open ou SQL99 de l’exception.  
  
-   getErrorCode retourne le numéro d’erreur de base de données spécifique.  
  
-   getMessage retourne le texte complet de l’exception. Le texte du message d'erreur décrit le problème et inclut souvent des espaces réservés pour des informations, tels que des noms d'objets insérés dans le message d'erreur lors de son affichage.  
  
-   getNextException retourne l’objet de SQLServerException suivant ou null si aucun objet d’exception plus à retourner.  
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est passée à la fonction et une instruction SQL incorrecte est créée, qui ne contient pas de clause FROM. Ensuite, l'instruction est exécutée et une exception SQL est traitée.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a> Voir aussi  
 [Diagnostic des problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
