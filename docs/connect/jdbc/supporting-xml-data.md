---
title: Prise en charge des données XML | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: af528f507f39cde948ae269d58abb2c0d9dcce46
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004279"
---
# <a name="supporting-xml-data"></a>Prise en charge des données XML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propose un type de données **xml** qui vous permet de stocker des documents et des fragments XML dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le type de données **xml** est intégré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et s’apparente à certains égards à d’autres types intégrés, tels que **int** et **varchar**. Comme d’autres types intégrés, vous pouvez utiliser le type de données **xml** comme type de variable, type de paramètre, type de retour de fonction ou type de colonne lors de la création d’une table, ou dans les fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST et CONVERT. Dans le pilote JDBC, le type de données **xml** peut être mappé en tant que chaîne, tableau d’octets, flux, objet CLOB, objet BLOB ou objet SQLXML. Le mappage en tant que chaîne est le mappage par défaut.  
  
 Le pilote JDBC prend en charge l'API JDBC 4.0, ce qui permet l'introduction de l'interface SQLXML. L'interface SQLXML définit des méthodes d'interaction et de manipulation des données XML. **SQLXML** est un type de données JDBC 4,0 et il est mappé au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données **XML** . Par conséquent, pour pouvoir utiliser le type de données SQLXML dans vos applications, vous devez définir l'instruction classpath afin d'inclure le fichier sqljdbc4.jar. Si l'application tente d'utiliser le fichier sqljdbc3.jar lors de l'accès à l'objet SQLXML et à ses méthodes, une exception est levée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide toujours les données XML avant de les stocker dans la colonne de base de données. Les applications peuvent utiliser le type de données **SQLXML**, car le pilote JDBC le mappe automatiquement au type de données **xml**. La prise en charge **SQLXML** est disponible dans sqljdbc4.jar. Pour obtenir la liste des versions de JRE prises en charge par [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], voir [Configuration requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
 Les rubriques de cette section décrivent l’interface SQLXML et expliquent comment programmer avec le type de données **SQLXML** en utilisant les méthodes de l’API JDBC.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Interface SQLXML](../../connect/jdbc/sqlxml-interface.md)|Décrit l'interface SQLXML et ses méthodes.|  
|[Programmation avec SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Explique comment utiliser les méthodes de l’API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour stocker et récupérer des données XML à partir d’une base de données relationnelle à l’aide du type de données Java **SQLXML**. Contient également des informations sur les types d'objets SQLXML ; par ailleurs, elle dresse une liste des recommandations et limitations importantes relatives à l'utilisation des objets SQLXML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
