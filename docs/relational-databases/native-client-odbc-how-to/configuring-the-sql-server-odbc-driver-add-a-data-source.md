---
title: Ajouter une source de données (ODBC) Microsoft Docs
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
ms.openlocfilehash: 55ae4f357aa850f6b3ff4ba9cca0b59a2ccbc570
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298320"
---
# <a name="configuring-the-sql-server-odbc-driver---add-a-data-source"></a>Configuration du pilote ODBC SQL Server - Ajouter une source de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Avant d'utiliser des applications ODBC avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, vous devez savoir comment mettre à niveau la version des procédures stockées du catalogue sur les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et savoir comment ajouter, supprimer et tester des sources de données.  
  
  Vous pouvez ajouter une source de données en utilisant oDBC Administrator, programmatiquement (en utilisant [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)), ou en créant un fichier.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Pour ajouter une source de données à l'aide de l'Administrateur ODBC  
  
1.  Du **panneau**de contrôle , accédez aux **outils administratifs,** puis soit **aux sources de données ODBC (64 bits)** ou aux sources de données **ODBC (32 bits).** Vous pouvez également appeler l'exécutable odbcad32.exe.  
  
2.  Cliquez sur **l’utilisateur DSN**, **Système DSN**, ou **Fichier DSN** onglet, puis cliquez sur **Ajouter**.  
  
3.  Cliquez **sur SQL Server**, puis cliquez sur **Finition**.  
  
4.  Complétez les étapes de la **création d’une nouvelle source de données à SQL Server** Wizard.  
  
### <a name="to-add-a-data-source-programmatically"></a>Pour ajouter une source de données par programme  
  
1.  Appelez [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) avec le deuxième paramètre réglé pour ODBC_ADD_DSN ou ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Pour ajouter une source de données de fichier  
  
1.  Appelez [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) avec un paramètre SAVEFILE-file_name dans la chaîne de connexion. Si la connexion est un succès, le pilote ODBC crée une source de données de fichier avec les paramètres de connexion dans l'emplacement désigné par le paramètre SAVEFILE.  
  
## <a name="see-also"></a>Voir aussi  
[Supprimer une source de données &#40;&#41;ODBC](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-delete-a-data-source.md)    
  
  
