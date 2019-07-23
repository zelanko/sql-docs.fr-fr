---
title: Utilisation des métadonnées du jeu de résultats | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86e41f52ed8296c46cfd7b167407b10fc9f0b285
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005944"
---
# <a name="using-result-set-metadata"></a>Utilisation des métadonnées du jeu de résultats

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour pouvoir interroger un jeu de résultats afin d’obtenir des informations sur les colonnes qu’il contient, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implémente la classe [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md). Cette classe contient plusieurs méthodes retournant des informations sous la forme d'une valeur unique.

Pour créer un objet SQLServerResultSetMetaData, vous pouvez utiliser la méthode [GetMetadata](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) .

Dans l’exemple suivant, une connexion ouverte à l' [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] exemple de base de données est transmise à la fonction, la méthode GetMetadata de la classe SQLServerResultSet est utilisée pour retourner un objet SQLServerResultSetMetaData, puis diverses méthodes de l’objet L’objet SQLServerResultSetMetaData est utilisé pour afficher des informations sur le nom et le type de données des colonnes contenues dans le jeu de résultats.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>Voir aussi

[Gestion des métadonnées avec le pilote JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
