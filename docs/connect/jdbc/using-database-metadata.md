---
title: Utilisation des métadonnées de base de données | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fce2bf9d72136b303ee3bc974f3aede313233a82
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026418"
---
# <a name="using-database-metadata"></a>Utilisation des métadonnées de base de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour interroger une base de données afin de recueillir des informations sur ce qu’elle prend en charge, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implémente la classe [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Cette classe contient plusieurs méthodes qui retournent des informations sous la forme d'une valeur unique ou d'un jeu de valeurs.

Pour créer un objet SQLServerDatabaseMetaData, vous pouvez utiliser la méthode [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) pour obtenir des informations concernant la base de données.

Dans l’exemple suivant, une connexion ouverte à l' [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] exemple de base de données est transmise à la fonction, la méthode GetMetadata de la classe SQLServerConnection est utilisée pour retourner un objet SQLServerDatabaseMetaData, puis diverses méthodes de l’objet L’objet SQLServerDatabaseMetaData est utilisé pour afficher des informations sur le pilote, la version du pilote, le nom de la base de données et la version de la base de données.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>Voir aussi

[Gestion de métadonnées avec le pilote JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
