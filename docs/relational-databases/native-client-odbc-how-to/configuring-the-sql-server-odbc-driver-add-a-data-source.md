---
title: Ajouter une source de données (ODBC) | Microsoft Docs
description: Découvrez comment SQL Server pilote ODBC appelle des procédures stockées en tant que procédures stockées distantes dans SQL Server à l’aide du mécanisme d’appel de procédure stockée distante.
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 996f61412a26f3c1231159e328d56e740b8f1e19
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725090"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Configuration du pilote ODBC SQL Server - Ajouter une source de données
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Avant d'utiliser des applications ODBC avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, vous devez savoir comment mettre à niveau la version des procédures stockées du catalogue sur les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et savoir comment ajouter, supprimer et tester des sources de données.  
  
  Vous pouvez ajouter une source de données à l’aide de l’administrateur ODBC, par programmation (à l’aide de [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)) ou en créant un fichier.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Pour ajouter une source de données à l'aide de l'Administrateur ODBC  
  
1.  Dans le **panneau de configuration**, accédez à **Outils d’administration** , puis à **sources de données ODBC (64 bits)** ou sources de **données ODBC (32 bits)**. Vous pouvez également appeler l'exécutable odbcad32.exe.  
  
2.  Cliquez sur l’onglet **DSN utilisateur**, **système DSN**ou **fichier DSN** , puis cliquez sur **Ajouter**.  
  
3.  Cliquez sur **SQL Server**, puis sur **Terminer**.  
  
4.  Effectuez les étapes de l’Assistant **créer une nouvelle source de données pour SQL Server** .  
  
### <a name="to-add-a-data-source-programmatically"></a>Pour ajouter une source de données par programme  
  
1.  Appelez [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) avec le deuxième paramètre défini sur ODBC_ADD_DSN ou ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Pour ajouter une source de données de fichier  
  
1.  Appelez [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) avec un paramètre SAVEFILE = file_name dans la chaîne de connexion. Si la connexion est un succès, le pilote ODBC crée une source de données de fichier avec les paramètres de connexion dans l'emplacement désigné par le paramètre SAVEFILE.  
  
## <a name="see-also"></a>Voir aussi  
[Supprimer une source de données &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
