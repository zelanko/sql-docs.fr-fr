---
title: Ajouter une Source de données (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 822ac0f5d2e228a982368849ed1c409ef63765ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142253"
---
# <a name="add-a-data-source-odbc"></a>Ajouter une source de données (ODBC)
  Vous pouvez ajouter une source de données à l’aide de l’administrateur ODBC, par programmation (à l’aide de [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), ou en créant un fichier.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Pour ajouter une source de données à l'aide de l'Administrateur ODBC  
  
1.  À partir de la **le panneau de configuration**, accès **outils d’administration** , puis **des Sources de données (ODBC)**. Vous pouvez également appeler l'exécutable odbcad32.exe.  
  
2.  Cliquez sur le **DSN utilisateur**, **DSN système**, ou **DSN de fichier** onglet, puis cliquez sur **ajouter**.  
  
3.  Cliquez sur **SQL Server**, puis cliquez sur **Terminer**.  
  
4.  Suivez les étapes de l'Assistant Créer une nouvelle source de données vers SQL Server.  
  
### <a name="to-add-a-data-source-programmatically"></a>Pour ajouter une source de données par programme  
  
1.  Appelez [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) avec le deuxième paramètre défini sur ODBC_ADD_DSN ou sur ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Pour ajouter une source de données de fichier  
  
1.  Appelez [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) avec un SAVEFILE = nom_fichier des paramètres dans la chaîne de connexion. Si la connexion est un succès, le pilote ODBC crée une source de données de fichier avec les paramètres de connexion dans l'emplacement désigné par le paramètre SAVEFILE.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des rubriques de procédures de commande pilote SQL Server ODBC](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  