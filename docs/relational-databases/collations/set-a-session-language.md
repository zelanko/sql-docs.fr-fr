---
description: Définir une langue de session
title: Définir une langue de session | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2bc28b0a3852963e125ca861d2c2361f0c07ba8c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465640"
---
# <a name="set-a-session-language"></a>Définir une langue de session
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  La langue de la session permet de définir le mode d'affichage des éléments suivants sur le serveur, en fonction des préférences linguistiques et culturelles :  
  
-   Langue utilisée pour les messages d'erreur et autres messages système. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère plusieurs copies de tous les messages d'erreur et système dans toutes les langues dans lesquelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est disponible. Ces messages peuvent être affichés à l'aide de la vue catalogue [sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) . Lorsque vous installez une version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ces messages système sont traduits pour la version linguistique installée. Par défaut, vous disposez également de l'ensemble des messages en anglais. De plus, vous pouvez ajouter des messages définis par l’utilisateur dans une langue spécifique à l’aide de [sp_addmessage](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
  
-   Format des données de date et d'heure.  
  
-   Noms des jours et des mois, y compris les abréviations.  
  
-   Premier jour de la semaine.  
  
-   Données de devise.  
  
 33 langues sont disponibles dans le cadre des paramètres de session. Pour obtenir la liste des langues, consultez [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).  
  
## <a name="setting-the-session-language-from-the-server"></a>Définition de la langue de session à partir du serveur  
 Pour définir la langue de la session à partir du serveur, utilisez [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="setting-the-session-language-from-the-client"></a>Définition de la langue de session à partir du client  
 La langue de la session peut être définie côté client via OLE DB, ODBC ou ADO.NET. Pour OLE DB, utilisez la propriété SSPROP_INIT_CURRENTLANGUAGE. Pour plus d’informations, consultez [Propriétés d’initialisation et d’autorisation](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 Pour ODBC, utilisez le mot clé Language. Pour plus d’informations, consultez [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Pour ADO.NET, utilisez le paramètre **Current Language** de l'objet **ConnectionString** . Pour plus d'informations, consultez la documentation du Kit de développement logiciel (SDK) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC).  
  
  
