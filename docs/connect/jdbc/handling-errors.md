---
title: Gestion des erreurs | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a5a30d85dedb8de9d5cbfcff1714731c04fcd66
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="handling-errors"></a>Gestion des erreurs
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous utilisez la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], toutes les conditions d’erreur de base de données sont renvoyées à votre application Java en tant qu’exceptions à l’aide de la [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) classe. Les méthodes suivantes de la classe SQLServerException sont héritées de java.sql.SQLException et java.lang.Throwable et ; et ils peuvent être utilisés pour retourner des informations spécifiques sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] erreur s’est produite :  
  
-   getSQLState retourne le standard X / Open ou SQL99 code d’état de l’exception.  
  
-   getErrorCode retourne le numéro d’erreur de base de données spécifique.  
  
-   getMessage renvoie le texte complet de l’exception. Le texte du message d'erreur décrit le problème et inclut souvent des espaces réservés pour des informations, tels que des noms d'objets insérés dans le message d'erreur lors de son affichage.  
  
-   getNextException retourne l’objet SQLServerException suivant ou null si aucun objet d’exception plus à retourner.  
  
 Dans l’exemple suivant, une connexion ouverte à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de données est transmise à la fonction et d’une instruction SQL incorrecte est créée, qui ne dispose pas d’une clause FROM. Ensuite, l'instruction est exécutée et une exception SQL est traitée.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic des problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
