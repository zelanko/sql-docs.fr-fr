---
title: Gestion des métadonnées avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7dc3913728eb2292088af6a2c84141749715c1c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850017"
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Gestion de métadonnées avec le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet d’utiliser des métadonnées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de plusieurs façons. Le pilote JDBC permet d'obtenir des métadonnées sur la base de données, un jeu de résultats ou des paramètres.  
  
 Le pilote JDBC fournit trois classes pour l’extraction de métadonnées d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) permet de retourner des informations sur la base de données actuellement connectée.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) permet de retourner des informations sur le jeu de résultats.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) permet de retourner des informations sur les paramètres des instructions préparées et qui peuvent être appelées.  
  
 Les rubriques de cette section décrivent l’utilisation de chacune des trois classes de métadonnées pour travailler sur des métadonnées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Les méthodes de métadonnées décrites dans cette section étant généralement coûteuses en termes de performances de l'application, il convient d'être prudent en ce qui concerne leur utilisation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Utilisation des métadonnées de base de données](../../connect/jdbc/using-database-metadata.md)|Décrit la procédure d'extraction des informations de métadonnées concernant la base de données actuellement connectée.|  
|[Utilisation des métadonnées d’un jeu de résultats](../../connect/jdbc/using-result-set-metadata.md)|Décrit la procédure d'extraction des informations de métadonnées concernant le jeu de résultats actuel.|  
|[Utilisation des métadonnées de paramètre](../../connect/jdbc/using-parameter-metadata.md)|Décrit la procédure d'extraction des informations de métadonnées sur les paramètres d'instructions préparées et pouvant être appelées.|  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
