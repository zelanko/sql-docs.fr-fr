---
title: "La gestion des métadonnées avec le pilote JDBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63d691c8bef93ad734a7596532ba567708128a2d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Gestion de métadonnées avec le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] peut être utilisé pour travailler avec des métadonnées dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données de différentes façons. Le pilote JDBC permet d'obtenir des métadonnées sur la base de données, un jeu de résultats ou des paramètres.  
  
 Le pilote JDBC fournit trois classes pour la récupération de métadonnées à partir d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données :  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), qui sert à retourner des informations sur la base de données qui est actuellement connecté.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), qui sert à retourner des informations sur le jeu de résultats.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), qui est utilisé pour retourner des informations sur les paramètres des instructions préparées et pouvant être appelées.  
  
 Les rubriques de cette section décrivent comment vous pouvez utiliser chacune des trois classes de métadonnées pour travailler avec des métadonnées dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données.  
  
> [!NOTE]  
>  Les méthodes de métadonnées décrites dans cette section étant généralement coûteuses en termes de performances de l'application, il convient d'être prudent en ce qui concerne leur utilisation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[À l’aide de métadonnées de la base de données](../../connect/jdbc/using-database-metadata.md)|Décrit la procédure d'extraction des informations de métadonnées concernant la base de données actuellement connectée.|  
|[Métadonnées du jeu à l’aide des résultats](../../connect/jdbc/using-result-set-metadata.md)|Décrit la procédure d'extraction des informations de métadonnées concernant le jeu de résultats actuel.|  
|[À l’aide des métadonnées de paramètre](../../connect/jdbc/using-parameter-metadata.md)|Décrit la procédure d'extraction des informations de métadonnées sur les paramètres d'instructions préparées et pouvant être appelées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
