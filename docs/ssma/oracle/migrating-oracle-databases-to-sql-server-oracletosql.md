---
title: Bases de données de migration d’Oracle vers SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 9e746d1df201349011d24fc0de007c74ba0073b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651187"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migration de bases de données Oracle vers SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) pour Oracle est un environnement complet qui vous permet de migrer rapidement des bases de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], base de données SQL Azure ou Azure SQL Data Warehouse. À l’aide de SSMA pour Oracle, vous pouvez passer en revue les objets de base de données et de données, évaluer les bases de données pour la migration, migrer des objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], base de données SQL Azure ou Azure SQL Data Warehouse, puis migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], base de données SQL Azure ou de données SQL Azure Entrepôt. Notez que vous ne pouvez pas migrer les schémas SYS et système Oracle.
  
## <a name="recommended-migration-process"></a>Processus de Migration recommandé  
Pour pouvoir migrer des objets et des données à partir de bases de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], base de données SQL Azure ou Azure SQL Data Warehouse, procédez comme suit :
  
1.  [Créez un projet SSMA](working-with-ssma-projects-oracletosql.md).  
  
    Après avoir créé le projet, vous pouvez définir les options de mappage de type, la migration et la conversion du projet. Pour plus d’informations sur les paramètres de projet, consultez [définition des Options de projet &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [Oracle de mappage et les Types de données SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Se connecter au serveur de base de données Oracle](connecting-to-oracle-database-oracletosql.md).  
  
3.  [Se connecter à une instance de SQL Server](connecting-to-sql-server-oracletosql.md).  
  
4.  [Mapper des schémas de base de données Oracle à des schémas de base de données SQL Server](mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
5.  Si vous le souhaitez, [créer des rapports d’évaluation](assessing-oracle-schemas-for-conversion-oracletosql.md) pour évaluer certains objets de base de données pour la conversion et estimer le temps de conversion.  
  
6.  [Convertir des schémas de base de données Oracle en schémas SQL Server](converting-oracle-schemas-oracletosql.md).  
  
7.  [Charger les objets de base de données convertis dans SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
    Vous pouvez effectuer cela dans une des manières suivantes :  
  
    -   Enregistrer un script et exécutez-le dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Synchroniser les objets de base de données.  
  
8.  [Migrer des données vers SQL Server](migrating-oracle-data-into-sql-server-oracletosql.md).  
  
9. Si nécessaire, mettre à jour des applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Bien démarrer avec SSMA pour Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
