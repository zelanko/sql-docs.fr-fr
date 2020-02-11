---
title: SQL Server Native Client des sources de données ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de1226d675859312e1ccaf908141586f865c8946
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63028386"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Sources de données ODBC SQL Server Native Client
  Un nom de source de données (DSN) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifie une source de données ODBC qui contient toutes les informations nécessaires à une application ODBC pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un serveur spécifique. Il existe deux moyens de définir un nom de source de données ODBC :  
  
-   Sur un ordinateur client, ouvrez outils d’administration dans le panneau de configuration, puis double-cliquez sur **sources de données (ODBC)**. L'Administrateur de sources de données ODBC qui vous permet de créer un DSN s'ouvre.  
  
-   Dans une application ODBC, appelez [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).  
  
 Une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient les éléments suivants :  
  
-   Nom de la source de données.  
  
-   Toutes les informations nécessaires pour se connecter à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Base de données par défaut à utiliser dans une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (facultatif).  
  
-   Paramètres tels que les options ANSI à utiliser, le besoin ou non d'enregistrer des statistiques de performance, et ainsi de suite (facultatif).  
  
 Aucune application ODBC n'est requise pour se connecter via une source de données. En revanche, l'application doit fournir les mêmes informations de connectivité à une fonction de connexion ODBC que celles que trouverait le pilote dans un DSN.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
