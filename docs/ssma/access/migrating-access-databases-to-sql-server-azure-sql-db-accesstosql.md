---
title: Migrer des bases de données Access vers SQL Server - base de données SQL Azure | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: b15ecd732acf373dbc5cee817983305c1d792fe4
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453591"
---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>Migration bases de données Access vers SQL Server - Azure SQL DB (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) est un outil qui fournit un environnement complet qui vous permet de migrer rapidement des bases de données Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. À l’aide de SSMA, vous pouvez consulter des accès et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure des objets de base de données, évaluer la base de données Access pour la migration, convertir des objets de base de données Access, chargez-les dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, puis migrer les données.  
  
## <a name="recommended-migration-process"></a>Processus de migration recommandée  
Pour pouvoir migrer des objets et des données à partir de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, procédez comme suit :  
  
1.  [Créez un projet SSMA](creating-and-managing-projects-accesstosql.md). Après avoir créé le projet, vous pouvez [définir les options de projet](setting-conversion-and-migration-options-accesstosql.md), y compris les options de conversion, les options de migration et les mappages de types de données.  
  
2.  [Ajouter des fichiers de base de données Access](adding-and-removing-access-database-files-accesstosql.md) au projet.  
  
    Vous pouvez ajouter des fichiers individuels, y compris les fichiers que vous trouvez sur l’ordinateur ou le réseau.  
  
3.  [Se connecter à l’instance cible de SQL Server](connecting-to-sql-server-accesstosql.md) ou [se connecter à l’instance cible de SQL Azure](connecting-to-azure-sql-db-accesstosql.md).  
  
    Vous pouvez vous connecter à SQL Server ou SQL Azure.  
  
4.  Pour personnaliser le mappage entre une ou plusieurs bases de données Access et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les schémas de SQL Azure, [mapper les bases de données source et cible](mapping-source-and-target-databases-accesstosql.md).  
  
5.  Si vous le souhaitez, vous pouvez [créer un rapport d’évaluation](assessing-access-database-objects-for-conversion-accesstosql.md) pour déterminer si les objets de base de données Access peuvent être convertis à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
6.  [Convertir des objets de base de données Access](converting-access-database-objects-accesstosql.md) à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou définitions d’objets SQL Azure.  
  
7.  [Charger les objets de base de données convertis dans SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
    Vous pouvez charger soit les objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure à l’aide de SSMA, ou vous pouvez enregistrer [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.  
  
8.  [Migrer d’accéder aux données dans SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
    > [!NOTE]  
    > Vous pouvez convertir, charger et migrer les schémas et les données en une seule étape. Pour effectuer la migration d’un seul clic, cliquez sur le **convertir, charger et migrer** bouton.  
  
9. Si vous souhaitez que vos applications Access à utiliser les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, utilisez [lier les tables de l’accès aux tables SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
Vous pouvez également utiliser l’Assistant de Migration pour vous guider tout au long de ce processus. Pour plus d’informations, consultez [Assistant Migration](migration-wizard-accesstosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Mise en route avec SQL Server Migration Assistant pour Access](getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Préparation des bases de données Access pour la Migration](preparing-access-databases-for-migration-accesstosql.md)
