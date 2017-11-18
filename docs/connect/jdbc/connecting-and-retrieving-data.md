---
title: "Connexion et l’extraction de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 506a577f8a1623a31ccb0901b00a3376b72ef262
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-and-retrieving-data"></a>Connexion et extraction de données
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous travaillez avec le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], il existe deux méthodes principales pour établir une connexion à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données. Consiste à définir les propriétés de connexion dans l’URL de connexion, puis appelez la méthode getConnection de la classe DriverManager pour retourner un [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) objet.  
  
> [!NOTE]  
>  Pour obtenir la liste des propriétés de connexion pris en charge par le pilote JDBC, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 La seconde méthode implique la définition des propriétés de connexion à l’aide de méthodes setter de la [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) classe, puis en appelant le [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) méthode pour retourner une SQLServerConnection objet.  
  
 Les rubriques de cette section décrivent les différentes façons dans laquelle vous pouvez vous connecter à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données et elles présentent également différentes techniques pour récupérer des données.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Exemple d’URL de connexion](../../connect/jdbc/connection-url-sample.md)|Décrit comment utiliser une URL de connexion pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , puis utilisez une instruction SQL pour récupérer des données.|  
|[Exemple de source de données](../../connect/jdbc/data-source-sample.md)|Décrit l'utilisation d'une source de données pour se connecter à SQL Server et l'utilisation d'une procédure stockée pour extraire des données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’applications JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  

