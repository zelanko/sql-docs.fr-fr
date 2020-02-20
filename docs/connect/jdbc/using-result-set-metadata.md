---
title: Utiliser les métadonnées d’un jeu de résultats | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ed0b1eedcafa1fab59d17f756523fc0fc189200
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026122"
---
# <a name="using-result-set-metadata"></a>Utilisation des métadonnées du jeu de résultats

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour pouvoir interroger un jeu de résultats afin d’obtenir des informations sur les colonnes qu’il contient, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implémente la classe [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md). Cette classe contient plusieurs méthodes retournant des informations sous la forme d'une valeur unique.

Pour créer un objet SQLServerResultSetMetaData, vous pouvez utiliser la méthode [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, la méthode getMetaData de la classe SQLServerResultSet est utilisée pour retourner un objet SQLServerResultSetMetaData, puis diverses méthodes de l’objet SQLServerResultSetMetaData sont employées pour afficher des informations sur le nom et le type de données des colonnes contenues dans le jeu de résultats.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>Voir aussi

[Gestion de métadonnées avec le pilote JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
