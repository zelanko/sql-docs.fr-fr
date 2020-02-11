---
title: Migration de bases de données Oracle vers SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: e1021643d503e1ca77f120b81046b3773f8ff458
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68259102"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migration de bases de données Oracle vers SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Assistant Migration (SSMA) pour Oracle est un environnement complet qui vous aide à migrer rapidement des bases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de données Oracle vers, Azure SQL DB ou Azure SQL Data Warehouse. En utilisant SSMA pour Oracle, vous pouvez examiner les données et les objets de base de données, évaluer les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pour la migration, migrer des objets de base de données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], azure SQL dB ou Azure SQL Data Warehouse, puis migrer des données vers, azure SQL dB ou Azure SQL Data Warehouse. Notez que vous ne pouvez pas migrer les schémas SYS et Oracle SYSTEM.
  
## <a name="recommended-migration-process"></a>Processus de migration recommandé  
Pour migrer des objets et des données de bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données Oracle vers, Azure SQL DB ou Azure SQL Data Warehouse, procédez comme suit :
  
1.  [Créez un nouveau projet SSMA](working-with-ssma-projects-oracletosql.md).  
  
    Après avoir créé le projet, vous pouvez définir les options de conversion de projet, de migration et de mappage de type. Pour plus d’informations sur les paramètres de projet, consultez [définition des options de projet &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [mappage des types de données Oracle et SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Connectez-vous au serveur de base de données Oracle](connecting-to-oracle-database-oracletosql.md).  
  
3.  [Connectez-vous à une instance de SQL Server](connecting-to-sql-server-oracletosql.md).  
  
4.  [Mappez les schémas de base de données Oracle aux schémas de base de données SQL Server](mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
5.  Vous pouvez également [créer des rapports d’évaluation](assessing-oracle-schemas-for-conversion-oracletosql.md) pour évaluer les objets de base de données pour la conversion et estimer la durée de la conversion.  
  
6.  [Convertit les schémas de base de données Oracle en schémas SQL Server](converting-oracle-schemas-oracletosql.md).  
  
7.  [Chargez les objets de base de données convertis dans SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
    Vous pouvez le faire de l’une des manières suivantes :  
  
    -   Enregistrez un script et exécutez-le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans.  
  
    -   Synchronisez les objets de base de données.  
  
8.  [Migrez les données vers SQL Server](migrating-oracle-data-into-sql-server-oracletosql.md).  
  
9. Si nécessaire, mettez à jour les applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Prise en main avec SSMA pour Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
