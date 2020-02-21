---
title: Utilisation de la fonction Holdability | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1c126385955ce6e9fa9098ec5a09ba115b94ffb0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026200"
---
# <a name="using-holdability"></a>Utilisation de la fonctionnalité de mise en attente

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Par défaut, un jeu de résultats créé dans une transaction est maintenu ouvert après la validation de la transaction dans la base de données ou lors de sa restauration. Cependant, il est parfois utile de fermer le jeu de résultats une fois que la transaction a été validée. Pour ce faire, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’utilisation de la fonctionnalité de mise en attente du jeu de résultats.

La fonctionnalité de mise en attente du jeu de résultats peut être définie à l’aide de la méthode [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Lors de la définition de la fonctionnalité de mise en attente à l'aide de la méthode setHoldability, les constantes de la fonctionnalité de mise en attente du jeu de résultats `ResultSet.HOLD_CURSORS_OVER_COMMIT` ou `ResultSet.CLOSE_CURSORS_AT_COMMIT` peuvent être utilisées.

Le pilote JDBC prend également en charge la définition de la fonctionnalité de mise en attente lors de la création de l'un des objets Statement. Lors de la création d'objets Statement qui ont des surcharges avec des paramètres de fonctionnalité de mise en attente du jeu de résultats, la fonctionnalité de mise en attente de l'objet statement doit correspondre à la fonctionnalité de mise en attente de la connexion. En l'absence de correspondance, une exception est levée. En effet, SQL Server prend en charge la fonctionnalité de mise en attente uniquement au niveau de la connexion.

La fonctionnalité de mise en attente d’un jeu de résultats représente la fonctionnalité de mise en attente de l’objet SQLServerConnection qui est associé au jeu de résultats lors de la création de ce dernier pour les curseurs côté serveur uniquement. Cela ne s'applique pas aux curseurs côté client. Tous les jeux de résultats avec des curseurs côté client ont toujours la valeur de fonctionnalité de mise en attente `ResultSet.HOLD_CURSORS_OVER_COMMIT`.

Pour les curseurs côté serveur, lors d'une connexion à SQL Server 2005 ou ultérieur, la définition de la fonctionnalité de mise en attente affecte uniquement la fonctionnalité des nouveaux jeux de résultats qui doivent être créés sur cette connexion. En d'autres termes, la définition de la fonctionnalité de mise en attente n'a aucun impact sur la fonctionnalité de mise en attente des jeux de résultats qui ont été créés antérieurement et qui sont déjà ouverts sur cette connexion.

Dans l’exemple suivant, la fonctionnalité de mise en attente du jeu de résultats est définie durant l’exécution d’une transaction locale composée de deux instructions séparées dans le bloc `try`. Les instructions sont exécutées sur la table Production.ScrapReason dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Tout d'abord, l'exemple passe en mode de transaction manuelle en définissant la validation automatique avec la valeur `false`. Une fois le mode de validation automatique désactivé, aucune instruction SQL n’est validée tant que l’application n’appelle pas explicitement la méthode [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md). Le code dans le bloc catch restaure la transaction si une exception est levée.

[!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]

## <a name="see-also"></a>Voir aussi

[Réalisation de transactions avec le pilote JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
