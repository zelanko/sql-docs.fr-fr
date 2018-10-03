---
title: Migrer des bases de données MySQL vers SQL Server - base de données SQL Azure | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: badfb3afaeba92f366e62fce8dfcb3ec7dae9f29
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626920"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>Migration des bases de données de MySQL vers SQL Server - Azure SQL DB (MySQLToSql)
SQL Server Migration Assistant (SSMA) pour MySQL est un environnement complet qui vous permet de migrer rapidement des bases de données MySQL vers SQL Server ou SQL Azure. À l’aide de SSMA pour MySQL, vous pouvez passez en revue les données et des objets de base de données, évaluer les bases de données pour la migration, migrer des objets de base de données vers SQL Server ou SQL Azure, puis migrer les données vers SQL Server ou SQL Azure.  
  
## <a name="recommended-migration-process"></a>Processus de Migration recommandé  
Pour migrer des objets et des données à partir de bases de données MySQL vers SQL Server ou SQL Azure, procédez comme suit :  
  
1.  [Utilisation de projets SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    Après avoir créé le projet, vous pouvez définir les options de mappage de type, la migration et la conversion du projet. Pour plus d’informations sur les paramètres du projet, consultez [définition des Options de projet &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [MySQL de mappage et les Types de données SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Connexion à MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Connexion à SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Mappage des bases de données MySQL à des schémas SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Connexion à la base de données SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  Si vous le souhaitez, [évaluation de bases de données MySQL pour la Conversion &#40;MySQLToSQL&#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) pour évaluer certains objets de base de données pour la conversion et estimer le temps de conversion.  
  
7.  [Conversion de bases de données MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Synchronisation](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. Vous pouvez effectuer cela dans une des manières suivantes :  
  
    -   Enregistrer un script et exécutez-le sur SQL Server ou SQL Azure.  
  
    -   Synchroniser les objets de base de données.  
  
10. [Migration de données MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. Si nécessaire, mettre à jour des applications de base de données.  
  
> [!NOTE]  
> Vous ne pouvez pas migrer les schémas Information_schema et MySQL.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Bien démarrer avec SSMA pour MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
