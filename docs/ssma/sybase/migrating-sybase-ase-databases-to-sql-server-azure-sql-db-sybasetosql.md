---
title: Migrer des bases de données Sybase ASE vers SQL Server-Azure SQL DB | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c3735e03e3196f899ab33ca152364244e3331ac5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028851"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Migration de bases de données SAP ASE vers SQL Server Azure SQL Database (SybaseToSQL)
Assistant Migration SQL Server (SSMA) pour SAP Adaptive Server Enterprise (ASE) est un environnement complet qui vous permet de migrer rapidement des bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données SAP ASE vers ou Azure SQL Database. En utilisant SSMA pour SAP ASE, vous pouvez examiner les données et les objets de base de données, évaluer les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la migration, migrer des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données vers ou Azure SQL Database, puis migrer des données vers ou Azure SQL Database.  
  
## <a name="recommended-migration-process"></a>Processus de migration recommandé  
Pour migrer des objets et des données de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SAP ASE vers ou Azure SQL Database, procédez comme suit :  
  
1.  [Créez un nouveau projet SSMA](working-with-ssma-projects-sybasetosql.md).  
  
    Après avoir créé le projet, vous pouvez définir les options de conversion de projet, de migration et de mappage de type. Pour plus d’informations sur les paramètres de projet, consultez [définition des options de projet &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [mappage des types de données Sybase ASE et SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Connectez-vous au serveur de base de données SAP ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
3.  [Connectez-vous à une instance SQL Server](connecting-to-sql-server-sybasetosql.md) ou [Connectez-vous à une instance de Azure SQL Database](connecting-to-azure-sql-db-sybasetosql.md).  
  
4.  [Mappez les schémas de base de données SAP ASE aux schémas de base de données SQL Server/Azure SQL Database](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Vous pouvez également [créer des rapports d’évaluation](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) pour évaluer les objets de base de données pour la conversion et estimer la durée de la conversion.  
  
6.  [Convertissez les schémas de base de données SAP ASE en schémas SQL Server/Azure SQL Database](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Chargez les objets de base de données convertis dans SQL Server/Azure SQL Database](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Vous pouvez enregistrer un script et l’exécuter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans ou Azure SQL Database, ou synchroniser les objets de base de données.  
  
8.  [Migrez les données vers SQL Server/Azure SQL Database](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Si nécessaire, mettez à jour vos applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Prise en main avec SSMA pour SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
