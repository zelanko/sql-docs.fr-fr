---
title: Sources de données ODBC SQL Server Native Client | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-communication
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8bda4a2221e0e91d45d9957ae0fb95bb661ce181
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Sources de données ODBC SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un nom de source de données (DSN) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifie une source de données ODBC qui contient toutes les informations nécessaires à une application ODBC pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un serveur spécifique. Il existe deux moyens de définir un nom de source de données ODBC :  
  
-   Sur un ordinateur client, ouvrez Outils d’administration dans le panneau de configuration, double-cliquez sur **des Sources de données (ODBC)**. L'Administrateur de sources de données ODBC qui vous permet de créer un DSN s'ouvre.  
  
-   Dans une application ODBC, appelez [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient les éléments suivants :  
  
-   Nom de la source de données.  
  
-   Toutes les informations nécessaires pour se connecter à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Base de données par défaut à utiliser dans une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (facultatif).  
  
-   Paramètres tels que les options ANSI à utiliser, le besoin ou non d'enregistrer des statistiques de performance, et ainsi de suite (facultatif).  
  
 Aucune application ODBC n'est requise pour se connecter via une source de données. En revanche, l'application doit fournir les mêmes informations de connectivité à une fonction de connexion ODBC que celles que trouverait le pilote dans un DSN.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
