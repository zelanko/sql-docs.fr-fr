---
title: Obtention de la version du pilote | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db44a391c16a63d28057c99755018179d6c2c0b5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028043"
---
# <a name="getting-the-driver-version"></a>Obtention de la version du pilote
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il existe plusieurs moyens d’identifier la version installée de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] :  
  
-   Appelez les méthodes [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)[getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) ou [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md).  
  
-   La version est affichée dans le fichier lisezmoi.txt de la distribution de produit.  
  
 De plus, le nom du pilote JDBC peut être retourné par l’appel de la méthode [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) sur la classe SQLServerDatabaseMetaData. Cet appel retourne, par exemple, « Microsoft JDBC Driver 6.4 for SQL Server ».  
  
 Voici un exemple de sortie des appels aux méthodes de la classe SQLServerDatabaseMetaData :  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Où « xxx.x » est le numéro de version finale.  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic de problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
