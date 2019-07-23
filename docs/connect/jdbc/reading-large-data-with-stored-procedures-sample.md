---
title: Exemple de lecture de données volumineuses avec des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cbf339845bd23f1beb4f5cd0f3b3a380689a3120
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956122"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Exemple de lecture de données volumineuses avec des procédures stockées

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet exemple d'application du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] montre comment récupérer un paramètre OUT volumineux à partir d'une procédure stockée.

Le fichier de code de cet exemple, ExecuteStoredProcedure.java, se trouve à l'emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, l’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est nécessaire. Vous devez également définir le classpath de façon à inclure le fichier jar mssql-jdbc. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d’informations sur le fichier JAR à choisir, voir [Configuration requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

L’exemple crée la procédure stockée requise dans l' [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] exemple de base de données:

## <a name="example"></a>Exemple

Dans l’exemple suivant, le code établit une connexion à la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Il crée ensuite des exemples de données et met à jour la table Production.Document en utilisant une requête paramétrable. Il obtient ensuite le mode de mise en mémoire tampon adaptative avec la méthode [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), puis exécute la procédure stockée GetLargeDataValue. À partir de la version 2.0 du pilote JDBC, la propriété de connexion responseBuffering a par défaut la valeur « adaptive ».

Pour finir, l’exemple de code affiche les données retournées avec les paramètres OUT et montre également comment utiliser les méthodes `mark` et `reset` sur le flux pour relire une partie des données.

[!code[JDBC#UsingAdaptiveBuffering2](../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>Voir aussi

[Utilisation de données volumineuses](../../connect/jdbc/working-with-large-data.md)
