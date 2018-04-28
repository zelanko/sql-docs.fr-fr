---
title: Classe SQLServerParameterMetaData | Documents Microsoft
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
ms.topic: article
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 54e6c4fd85ed8f658019d6a01a394317f764c9af
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverparametermetadata-class"></a>Classe SQLServerParameterMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente les métadonnées pour les paramètres d'instructions préparées.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.lang.Object  
  
 **Implémente :** java.sql.ParameterMetaData  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>Notes  
 Pour récupérer des métadonnées de paramètre, des instructions préparées sont exécutées avec SET FMT ONLY. Les instructions pouvant être appelées appellent sp_sproc_columns pour récupérer les noms et les métadonnées des paramètres de procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
