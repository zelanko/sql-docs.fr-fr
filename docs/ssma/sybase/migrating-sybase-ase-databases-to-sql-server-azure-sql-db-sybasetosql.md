---
title: Migrer des bases de données Sybase ASE vers SQL Server - base de données SQL Azure | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 96ade7125c0d03963e8e012ed72bdb8fdef492cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62705466"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Migration des bases de données SAP ASE vers SQL Server - Azure SQL Database (SybaseToSQL)
Migration Assistant SQL Server (SSMA) pour SAP Adaptive Server Enterprise (ASE) est un environnement complet qui vous permet de migrer rapidement des bases de données SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure. À l’aide de SSMA pour SAP ASE, vous pouvez passer en revue les objets de base de données et de données, évaluer les bases de données pour la migration, migrer des objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, et migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure.  
  
## <a name="recommended-migration-process"></a>Processus de migration recommandée  
Pour pouvoir migrer des objets et des données à partir de bases de données SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, procédez comme suit :  
  
1.  [Créez un projet SSMA](working-with-ssma-projects-sybasetosql.md).  
  
    Après avoir créé le projet, vous pouvez définir les options de mappage de type, la migration et la conversion du projet. Pour plus d’informations sur les paramètres de projet, consultez [définition des Options de projet &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [mappage des ASE Sybase et les Types de données SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Se connecter au serveur de base de données SAP ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
3.  [Se connecter à une instance SQL Server](connecting-to-sql-server-sybasetosql.md) ou [se connecter à une instance de base de données SQL Azure](connecting-to-azure-sql-db-sybasetosql.md).  
  
4.  [Mapper des schémas de base de données de SAP ASE à SQL Server / schémas de base de données Azure SQL Database](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Si vous le souhaitez, [créer des rapports d’évaluation](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) pour évaluer certains objets de base de données pour la conversion et estimer le temps de conversion.  
  
6.  [Convertir des schémas de base de données SAP ASE dans SQL Server / schémas de base de données SQL Azure](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Charger les objets de base de données convertis dans SQL Server / Azure SQL Database](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Enregistrer un script et l’exécuter dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure, ou de synchroniser les objets de base de données.  
  
8.  [Migrer des données vers SQL Server / Azure SQL Database](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Si nécessaire, mettez à jour vos applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Bien démarrer avec SSMA pour SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
