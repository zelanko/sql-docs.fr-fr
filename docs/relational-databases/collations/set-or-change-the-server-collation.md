---
description: Définir ou changer le classement du serveur
title: Définir ou changer le classement du serveur | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ddd5615aafaa52a6bd0bb672f144e51d497c183
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193433"
---
# <a name="set-or-change-the-server-collation"></a>Définir ou changer le classement du serveur

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Le classement du serveur agit en tant que classement par défaut pour toutes les bases de données système installées avec l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que pour toute base de données utilisateur nouvellement créée. Vous devez choisir avec soin le classement au niveau du serveur, car il affecte :
 - Les règles de tri et de comparaison dans `=`, `JOIN`, `ORDER BY` et d’autres opérateurs qui comparent les données textuelles.
 - Le classement des colonnes `CHAR`, `VARCHAR`, `NCHAR` et `NVARCHAR` dans les vues système, les fonctions système et les objets dans TempDB (par exemple, les tables temporaires).
 - Les noms des variables, des curseurs et des étiquettes `GOTO`. Les variables @pi et @PI sont considérées comme différentes si le classement au niveau du serveur respecte la casse et comme identiques si le classement au niveau du serveur respecte la casse.
  
## <a name="setting-the-server-collation-in-sql-server"></a>Définition du classement du serveur dans SQL Server

  Le classement du serveur est spécifié au cours de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le classement au niveau du serveur par défaut est basé sur les paramètres régionaux du système d’exploitation. Par exemple, le classement par défaut pour les systèmes utilisant l’anglais américain (en US) est **SQL_Latin1_General_CP1_CI_AS**. Les classements Unicode seulement ne peuvent pas être spécifiés comme classement au niveau du serveur. Pour plus d’informations, notamment la liste des paramètres régionaux de système d’exploitation pour les mappages de classement par défaut, consultez la section « classements au niveau du serveur » de [Classement et prise en charge d’Unicode](collation-and-unicode-support.md#Server-level-collations).

> [!NOTE]  
> Le classement au niveau du serveur pour la base de données locale Express [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est **SQL_Latin1_General_CP1_CI_AS** et ne peut pas être modifié, pendant ou après l’installation.  

## <a name="changing-the-server-collation-in-sql-server"></a>Changement du classement du serveur dans SQL Server

 La modification du classement du serveur par défaut pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut s'avérer une opération complexe et implique les étapes suivantes :  
  
- Vérifiez que vous disposez de toutes les informations ou de tous les scripts nécessaires pour recréer vos bases de données utilisateur et les objets qu'elles contiennent.  
  
- Exportez toutes vos données à l’aide d’un outil tel que l’ [utilitaire bcp](../../tools/bcp-utility.md). Pour plus d’informations, consultez [Importation et exportation en bloc de données &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
- Supprimez toutes les bases de données utilisateur.  
  
- Recréez la base de données MASTER en spécifiant le nouveau classement dans la propriété SQLCOLLATION de la commande **setup** . Par exemple :  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]
    /SQLCOLLATION=CollationName  
    ```  
  
     Pour plus d’informations, consultez [Reconstruire des bases de données système](../../relational-databases/databases/rebuild-system-databases.md).  
  
- Créez toutes les bases de données et tous les objets qu'elles contiennent.  
  
- Importez toutes vos données.  
  
> [!NOTE]  
> Au lieu de changer le classement par défaut d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier un classement par défaut pour chaque nouvelle base de données que vous créez via la clause `COLLATE` des instructions `CREATE DATABASE` et `ALTER DATABASE`. Pour plus d’informations, voir [Set or Change the Database Collation](set-or-change-the-database-collation.md).  
  
## <a name="setting-the-server-collation-in-managed-instance"></a>Définition du classement du serveur dans Managed Instance
Le classement au niveau du serveur dans Azure SQL Managed Instance peut être spécifié quand l’instance est créée et ne peut plus être modifiée. Vous pouvez définir le classement au niveau du serveur par le biais du [portail Azure](/azure/sql-database/sql-database-managed-instance-get-started#create-a-managed-instance) ou de [PowerShell et du modèle Resource Manager](/azure/sql-database/scripts/sql-managed-instance-create-powershell-azure-resource-manager-template) lors de la création de l’instance. Le classement par défaut au niveau du serveur est **SQL_Latin1_General_CP1_CI_AS**. Les classements Unicode seulement et les nouveaux classements UTF-8 ne peuvent pas être spécifiés comme classement au niveau du serveur.
Si vous migrez des bases de données depuis SQL Server vers Managed Instance, vérifiez le classement du serveur dans le serveur SQL Server source à l’aide de la fonction `SERVERPROPERTY(N'Collation')`, puis créez une instance Managed Instance qui correspond au classement de votre serveur SQL Server. La migration d’une base de données depuis SQL Server vers Managed Instance sans mise en correspondance des classements au niveau du serveur peut entraîner plusieurs erreurs inattendues dans les requêtes. Vous ne pouvez pas changer le classement au niveau du serveur sur l’instance Managed Instance existante.

## <a name="see-also"></a>Voir aussi

 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Définir ou modifier le classement de la base de données](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Définir ou modifier le classement des colonnes](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Reconstruire des bases de données système](../../relational-databases/databases/rebuild-system-databases.md)  
