---
title: Exécution d’opérations par lots | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a77816598e7c8e3f0589f71cb5c02e40e0e17317
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027922"
---
# <a name="performing-batch-operations"></a>Exécution d'opérations par lot
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour améliorer les performances d'exécution de plusieurs mises à jour d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet de les effectuer sous forme d'une seule unité de travail, également appelée lot.  
  
 Les classes [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) sont toutes utilisables pour soumettre des mises à jour par lot. La méthode [addBatch](../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md) permet d'ajouter une commande, la méthode [clearBatch](../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md) d'effacer la liste des commandes et la méthode [executeBatch](../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md) de soumettre toutes les commandes pour traitement. Seules des instructions DDL (Data Definition Language, langage de définition de données) et DML (Data Manipulation Language, langage de manipulation de données) qui retournent un seul nombre de mises à jour peuvent être exécutées dans un lot.  
  
 La méthode executeBatch retourne un tableau de valeurs **int** correspondant au nombre de mises à jour de chaque commande. Si l’une des commandes échoue, une BatchUpdateException est levée et vous devez utiliser la méthode getUpdateCounts de la classe BatchUpdateException pour récupérer le tableau de nombres de mises à jour. En cas d'échec d'une commande, le pilote continue à traiter les commandes restantes. Toutefois, si une commande contient une erreur de syntaxe, les instructions contenues dans le lot échouent.  
  
> [!NOTE]  
>  Si vous n’avez pas besoin d’utiliser les nombres de mises à jour, vous pouvez commencer par émettre une instruction SET NOCOUNT ON auprès de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ceci réduira le trafic réseau et améliorera les performances de votre application.  
  
 Par exemple, créez la table suivante dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] :  
  
```sql
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 Dans l'exemple suivant, une connexion ouverte à l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, la méthode addBatch est utilisée pour créer les instructions à exécuter et la méthode executeBatch est appelée pour soumettre le lot à la base de données.  
  
```java
public static void executeBatchUpdate(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('X', 100)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Y', 200)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Z', 300)");  
      int[] updateCounts = stmt.executeBatch();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
