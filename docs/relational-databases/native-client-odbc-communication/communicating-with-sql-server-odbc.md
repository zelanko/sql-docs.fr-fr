---
title: Communication avec SQL Server (ODBC) | Microsoft Docs
description: Découvrez comment une application ODBC communique avec une instance de SQL Server à l’aide de connexions et de ressources de connexion.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b6f149f8d1d714839d356d3675a19656f2ea7d53
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734903"
---
# <a name="communicating-with-sql-server-odbc"></a>Communication avec SQL Server (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Pour qu’une application ODBC communique avec une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , elle doit allouer des handles d’environnement et de connexion et se connecter à la source de données. Après avoir établi une connexion, l'application peut envoyer des requêtes au serveur et traiter tous les jeux de résultats. Lorsque l'application a terminé d'utiliser la source de données, elle se déconnecte de la source de données et libère le handle de connexion. Lorsque l'application a libéré tous ses handles de connexion, elle libère le handle d'environnement.  
  
 Une application peut se connecter à un nombre quelconque de sources de données. L'application peut utiliser une combinaison de pilotes et de sources de données, le même pilote et une combinaison de sources de données, voire le même pilote et plusieurs connexions à la même source de données.  
  
 Vous pouvez télécharger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les exemples ODBC Native Client à partir de la page de [téléchargements de SQL Server](https://go.microsoft.com/fwlink/?LinkId=62796) sur MSDN.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Allocation d'un handle d'environnement](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Allocation d'un handle de connexion](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [Sources de données ODBC SQL Server Native Client](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Connexion à une source de données &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Déconnexion d'une source de données](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;&#41;ODBC](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
