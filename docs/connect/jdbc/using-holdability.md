---
title: "À l’aide de la mise en attente | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19dfa43e83b3fe94fa75df6a2713497093a08a96
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-holdability"></a>Utilisation de la fonctionnalité de mise en attente
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Par défaut, un jeu de résultats créé dans une transaction est maintenu ouvert après la validation de la transaction dans la base de données ou lors de sa restauration. Cependant, il est parfois utile de fermer le jeu de résultats une fois que la transaction a été validée. Pour ce faire, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’utilisation de résultat mise en attente du jeu.  
  
 Mise en attente du jeu de résultats peut être définie à l’aide de la [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) méthode de la [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Lors de la définition de la fonctionnalité à l’aide de la méthode setHoldability, le jeu de résultats des constantes de mise en attente de ResultSet.HOLD_CURSORS_OVER_COMMIT ou ResultSet.CLOSE_CURSORS_AT_COMMIT peut être utilisé.  
  
 Le pilote JDBC prend également en charge la définition de la fonctionnalité de mise en attente lors de la création de l'un des objets Statement. Lors de la création d'objets Statement qui ont des surcharges avec des paramètres de fonctionnalité de mise en attente du jeu de résultats, la fonctionnalité de mise en attente de l'objet statement doit correspondre à la fonctionnalité de mise en attente de la connexion. En l'absence de correspondance, une exception est levée. En effet, SQL Server prend en charge la fonctionnalité de mise en attente uniquement au niveau de la connexion.  
  
 La fonctionnalité d’un jeu de résultats est la fonctionnalité de l’objet SQLServerConnection qui est associé à l’ensemble de résultats à l’heure de création de l’ensemble de résultats pour les curseurs côté serveur uniquement. Cela ne s'applique pas aux curseurs côté client. Tous les jeux de résultats avec des curseurs côté client aura toujours la valeur de la mise en attente de ResultSet.HOLD_CURSORS_OVER_COMMIT.  
  
 Pour les curseurs côté serveur, lors d'une connexion à SQL Server 2005 ou ultérieur, la définition de la fonctionnalité de mise en attente affecte uniquement la fonctionnalité des nouveaux jeux de résultats qui doivent être créés sur cette connexion. En d'autres termes, la définition de la fonctionnalité de mise en attente n'a aucun impact sur la fonctionnalité de mise en attente des jeux de résultats qui ont été créés antérieurement et qui sont déjà ouverts sur cette connexion. Toutefois, avec SQL Server 2000, la définition de la fonctionnalité de mise en attente affecte la fonctionnalité de mise en attente des jeux de résultats existants et des nouveaux jeux de résultats qui doivent être créés sur cette connexion.  
  
 Dans l’exemple suivant, la fonction holdability du jeu de résultats est définie lors de l’exécution d’une transaction locale composée de deux instructions distinctes dans la `try` bloc. Les instructions sont exécutées sur la table Production.ScrapReason dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de données exemple. Tout d’abord, l’exemple passe en mode de transaction manuelle en affectant à la validation automatique **false**. Une fois que le mode de validation automatique est désactivé, aucune instruction SQL ne peuvent être validées jusqu'à ce que l’application appelle la [validation](../../connect/jdbc/reference/commit-method-sqlserverconnection.md) méthode explicitement. Le code dans le bloc catch restaure la transaction si une exception est levée.  
  
 [!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de Transactions avec le pilote JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  

