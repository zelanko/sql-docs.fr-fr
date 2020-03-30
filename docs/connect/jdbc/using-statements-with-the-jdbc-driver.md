---
title: Utilisation d'instructions avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7f8f3e8f-841e-4449-9154-b5366870121f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9ddd61d15e3c363766c7e49b8e9045b60a7be164
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69025796"
---
# <a name="using-statements-with-the-jdbc-driver"></a>Utilisation d'instructions avec le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet d’utiliser les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de plusieurs façons. Vous pouvez utiliser le pilote JDBC pour appliquer des instructions SQL à la base de données ou pour appeler des procédures stockées dans la base de données en utilisant des paramètres d'entrée et de sortie. Le pilote JDBC prend également en charge l'utilisation de séquences d'échappement SQL, de nombres de mises à jour, de clés générées automatiquement, ainsi que l'exécution de mises à jour dans le cadre d'une opération par lot.  
  
Le pilote JDBC fournit trois classes pour l’extraction de données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1. [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) : permet d’exécuter des instructions SQL sans paramètres.  
  
2. [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) : (héritée de SQLServerStatement) permet d’exécuter des instructions SQL compilées pouvant contenir des paramètres IN.  
  
3. [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) : (héritée de SQLServerPreparedStatement) permet d’exécuter des procédures stockées pouvant contenir des paramètres IN et/ou OUT.  
  
 Les rubriques de cette section expliquent comment utiliser chacune des trois classes d’instructions pour travailler sur des données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Contenu de cette section  

| Rubrique                                                                                                    | Description                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Utilisation d'instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)                             | Décrit comment utiliser des instructions SQL avec le pilote JDBC pour travailler sur des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    |
| [Utilisation d'instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md) | Décrit comment utiliser des procédures stockées avec le pilote JDBC pour travailler sur des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. |
| [Utilisation de plusieurs jeux de résultats](../../connect/jdbc/using-multiple-result-sets.md)                           | Décrit l'utilisation du pilote JDBC pour extraire des données de plusieurs jeux de résultats.                                                                       |
| [Utilisation de séquences d'échappement SQL](../../connect/jdbc/using-sql-escape-sequences.md)                           | Décrit l'utilisation de séquences d'échappement SQL, telles que les littéraux et fonctions de date et d'heure.                                                               |
| [Utilisation de clés générées automatiquement](../../connect/jdbc/using-auto-generated-keys.md)                             | Décrit l'utilisation des clés générées automatiquement.                                                                                                     |
| [Exécution d'opérations par lot](../../connect/jdbc/performing-batch-operations.md)                         | Décrit l'utilisation du pilote JDBC pour effectuer des opérations par lot.                                                                                      |
| [Gestion d'instructions complexes](../../connect/jdbc/handling-complex-statements.md)                         | Décrit l'utilisation du pilote JDBC pour exécuter des instructions complexes effectuant plusieurs tâches et pouvant retourner différents types de données.               |
  
## <a name="see-also"></a>Voir aussi

[Présentation du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
