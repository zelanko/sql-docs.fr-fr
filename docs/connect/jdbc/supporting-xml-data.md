---
description: Prise en charge des données XML
title: Prendre en charge les données XML | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da49d5c0468f19768eff720e7f03690bea954432
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88396275"
---
# <a name="supporting-xml-data"></a>Prise en charge des données XML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propose un type de données **xml** qui vous permet de stocker des documents et des fragments XML dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le type de données **xml** est intégré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et s’apparente à certains égards à d’autres types intégrés, comme **int** et **varchar**. Comme d’autres types intégrés, vous pouvez utiliser le type de données **xml** comme type de variable, type de paramètre, type de retour de fonction ou type de colonne lors de la création d’une table, ou dans les fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST et CONVERT. Dans le pilote JDBC, le type de données **xml** peut être mappé en tant que chaîne, tableau d’octets, flux, objet CLOB, objet BLOB ou objet SQLXML. Le mappage en tant que chaîne est le mappage par défaut.  
  
 Le pilote JDBC prend en charge l'API JDBC 4.0, ce qui permet l'introduction de l'interface SQLXML. L'interface SQLXML définit des méthodes d'interaction et de manipulation des données XML. Le type de données JDBC 4.0 **SQLXML** correspond au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**xml**. Par conséquent, pour pouvoir utiliser le type de données SQLXML dans vos applications, vous devez définir l'instruction classpath afin d'inclure le fichier sqljdbc4.jar. Si l'application tente d'utiliser le fichier sqljdbc3.jar lors de l'accès à l'objet SQLXML et à ses méthodes, une exception est levée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide toujours les données XML avant de les stocker dans la colonne de base de données. Les applications peuvent utiliser le type de données **SQLXML**, car le pilote JDBC le mappe automatiquement au type de données **xml**. La prise en charge **SQLXML** est disponible dans sqljdbc4.jar. Pour obtenir la liste des versions de JRE prises en charge par [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], consultez [Configuration requise pour le pilote JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
 Les rubriques de cette section décrivent l’interface SQLXML et expliquent comment programmer avec le type de données **SQLXML** en utilisant les méthodes de l’API JDBC.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Interface SQLXML](../../connect/jdbc/sqlxml-interface.md)|Décrit l'interface SQLXML et ses méthodes.|  
|[Programmation à l'aide de SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Explique comment utiliser les méthodes de l’API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour stocker et récupérer des données XML à partir d’une base de données relationnelle à l’aide du type de données Java **SQLXML**. Contient également des informations sur les types d'objets SQLXML ; par ailleurs, elle dresse une liste des recommandations et limitations importantes relatives à l'utilisation des objets SQLXML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
