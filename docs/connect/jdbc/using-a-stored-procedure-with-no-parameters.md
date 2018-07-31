---
title: Utilisation d’une procédure stockée avec des paramètres d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7db021b9d3fdf875c2c6074159b56d8e6cb0fd14
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992921"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Utilisation d'une procédure stockée sans paramètres
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le type le plus simple de procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] que vous pouvez appeler ne contient pas de paramètres et retourne un seul jeu de résultats. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] intègre la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), que vous pouvez utiliser pour appeler ce type de procédure stockée et traiter les données qu’elle retourne.  
  
 Quand vous utilisez le pilote JDBC pour appeler une procédure stockée sans paramètres, vous devez utiliser la séquence d’échappement SQL `call`. La syntaxe de la séquence d’échappement `call` sans paramètres est la suivante :  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  Pour plus d’informations sur les séquences d’échappement SQL, consultez [à l’aide les séquences d’échappement SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Par exemple, créez la procédure stockée suivante dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] :  
  
```  
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 Cette procédure stockée retourne un seul jeu de résultats contenant une colonne de données affichant une combinaison des fonctions, des prénoms et des noms des dix premiers contacts figurant dans la table Person.Contact.  
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, et la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) est utilisée pour appeler la procédure stockée GetContactFormalNames.  
  
```  
public static void executeSprocNoParams(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
  
      while (rs.next()) {  
         System.out.println(rs.getString("FormalName"));  
      }  
      rs.close();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation d’instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
