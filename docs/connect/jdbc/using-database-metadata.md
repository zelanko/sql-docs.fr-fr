---
title: À l’aide de métadonnées de la base de données | Documents Microsoft
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
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7a93692028a5debc94d6bb35d38e2a4a64f01de
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-metadata"></a>Utilisation des métadonnées de base de données
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour interroger une base de données pour les informations qu’il prend en charge, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implémente la [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) classe. Cette classe contient plusieurs méthodes qui retournent des informations sous la forme d'une valeur unique ou d'un jeu de valeurs.  
  
 Pour créer un objet SQLServerDatabaseMetaData, vous pouvez utiliser la [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) méthode de la [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe pour obtenir des informations sur la base de données auquel elle est connectée.  
  
 Dans l’exemple suivant, une connexion ouverte à la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de données est transmise à la fonction, la méthode getMetaData de la classe SQLServerConnection est utilisée pour retourner un objet SQLServerDatabaseMetadata, puis diverses méthodes de la Objet SQLServerDatabaseMetaData permettent d’afficher des informations sur le pilote, version du pilote, nom de la base de données et version de base de données.  
  
 [!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des métadonnées avec le pilote JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
