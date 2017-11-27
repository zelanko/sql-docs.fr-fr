---
title: "À l’aide d’une instruction SQL pour modifier des objets de base de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c5bc8d1f8ce376595a2daf1cc8fddd240a2b4ba8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Utilisation d'une instruction SQL pour modifier les objets de base de données
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour modifier [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] des objets de base de données à l’aide d’une instruction SQL, vous pouvez utiliser la [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) méthode de la [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. La méthode executeUpdate transmet l’instruction SQL à la base de données pour le traitement et puis de retourner la valeur 0, car aucune ligne n’ont été affectés.  
  
 Pour ce faire, vous devez d’abord créer un objet SQLServerStatement à l’aide de la [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) méthode de la [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
> [!NOTE]  
>  Les instructions SQL qui modifient les objets dans une base de données sont des instructions dites DDL (Data Definition Language, langage de définition de données). Elles incluent des instructions telles que CREATE TABLE, DROP TABLE, CREATE INDEX et DROP INDEX. Pour plus d’informations sur les types d’instructions DDL qui sont pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], consultez [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
 Dans l’exemple suivant, une connexion ouverte à la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de données est transmise à la fonction, une instruction SQL est générée qui crée la TestTable simple dans la base de données, puis l’instruction est exécutée et la valeur de retour s’affiche.  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
