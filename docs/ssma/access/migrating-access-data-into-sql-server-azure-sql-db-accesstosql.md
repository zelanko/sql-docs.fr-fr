---
title: Migration de données Access vers SQL Server - Azure SQL DB (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d15d7608879d9116832e083654cc07717c72e23e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666468"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>Migration de données Access vers SQL Server - Azure SQL DB (AccessToSQL)
Une fois que vous avez créé les objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez migrer des données à partir de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
## <a name="setting-migration-options"></a>Définition des Options de Migration  
Avant de migrer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, passez en revue les options de migration de projet dans le **paramètres du projet** boîte de dialogue. Dans cette boîte de dialogue, vous pouvez définir la taille de lot de migration, le verrouillage de table, la contrainte de vérification, le déclencheur d’insertion se déclencher, identité et manipulation, d’une valeur null et comment gérer les dates qui sont hors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plage. Pour plus d’informations, consultez [paramètres du projet (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Migration de données  
Migration de données sont une opération de chargement en masse qui déplace les lignes de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure dans des transactions. Le nombre de lignes à charger dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de la migration, vérifiez que le volet de sortie est visible. Le cas contraire, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour migrer des données**  
  
1.  Assurez-vous que vous avez chargé les objets de base de données Access dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
2.  Dans l’Explorateur de métadonnées d’accès, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour une base de données entière, sélectionnez la case à cocher en regard du nom de la base de données.  
  
    -   Pour migrer des données à partir des tables individuelles, développez la base de données, puis **Tables**, puis sélectionnez la case à cocher en regard du tableau. Pour omettre les données à partir des tables individuelles, désactivez la case à cocher.  
  
3.  Avec le bouton droit **bases de données** , puis sélectionnez **migrer des données**.  
  
Vous pouvez également migrer des données en dehors de SSMA à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bcp** utilitaire de ligne de commande ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations sur ces outils, consultez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="next-step"></a>Étape suivante  
Si vous avez des applications de base de données Access que vous souhaitez continuer à utiliser après la migration, lier les tables de base de données d’accès à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des tables de SQL Azure. Pour plus d’informations, consultez [liaison d’Applications Access vers SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Conversion de paramètre et les Options de Migration](setting-conversion-and-migration-options-accesstosql.md)  
  
