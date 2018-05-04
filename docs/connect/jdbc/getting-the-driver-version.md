---
title: Obtention de la Version de pilote | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3828c04f418a31e2dacddb97472ec3b2f776a5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getting-the-driver-version"></a>Obtention de la version du pilote
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La version installée du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sont accessibles comme suit :  
  
-   Appelez le [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) méthodes [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md), ou [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md).  
  
-   La version est affichée dans le fichier lisezmoi.txt de la distribution de produit.  
  
 En outre, le nom du pilote JDBC peut être retourné à partir de la [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) appel de méthode sur la classe SQLServerDatabaseMetaData. Elle retourne, par exemple, « Microsoft JDBC Driver 6.4 pour SQL Server ».  
  
 Voici un exemple de la sortie des appels aux méthodes de la classe SQLServerDatabaseMetaData :  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Où « xxx.x » est le numéro de version finale.  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic des problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
