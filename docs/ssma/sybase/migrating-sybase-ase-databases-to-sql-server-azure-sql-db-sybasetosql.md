---
title: "Migrer des bases de données Sybase ASE à SQL Server - base de données SQL Azure | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63dc9188d93def41a5116386f93bf29e3b744e8e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-sybase-ase-databases-to-sql-server---azure-sql-db-sybasetosql"></a>Migration Sybase ASE bases de données SQL Server : base de données SQL Azure (SybaseToSQL)
SQL Server Migration Assistant (SSMA) pour Sybase est un environnement complet qui vous permet de migrer rapidement des bases de données Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure. À l’aide de SSMA pour Sybase, vous pouvez examiner les objets de base de données et les données, évaluer les bases de données pour la migration, migrer des objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure, puis migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou base de données SQL Azure.  
  
## <a name="recommended-migration-process"></a>Processus de Migration recommandé  
Pour pouvoir migrer des objets et des données à partir de bases de données ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou Azure SQL DB, procédez comme suit :  
  
1.  [Créez un projet SSMA](http://msdn.microsoft.com/en-us/11091d95-c488-48c3-891a-743cac94ac93).  
  
    Après avoir créé le projet, vous pouvez définir les options de mappage de type, de migration et de conversion de projet. Pour plus d’informations sur les paramètres de projet, consultez [définition des Options de projet &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md). Pour plus d’informations sur la personnalisation des mappages de types de données, consultez [ASE de Sybase mappage et les Types de données SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Se connecter au serveur de base de données Sybase ASE](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Se connecter à une instance SQL Server](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) ou [se connecter à une instance de base de données SQL Azure](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Mapper des schémas de base de données ASE à SQL Server / base de données SQL Azure database schémas](http://msdn.microsoft.com/en-us/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Si vous le souhaitez, [créer des rapports d’évaluation](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) pour évaluer des objets de base de données pour la conversion et estimer le temps de conversion.  
  
6.  [Convertir des schémas de base de données Sybase ASE dans SQL Server / schémas de base de données SQL Azure](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Charger les objets de base de données convertie dans SQL Server / base de données SQL Azure](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Vous pouvez par un enregistrement d’un script et exécutez-le dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou de la base de données SQL Azure, ou vous pouvez synchroniser les objets de base de données.  
  
8.  [Migrer les données vers SQL Server / base de données SQL Azure](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Si nécessaire, mettez à jour vos applications de base de données.  
  
## <a name="see-also"></a>Voir aussi  
[L’installation de SSMA pour Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Prise en main de SSMA pour Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  

