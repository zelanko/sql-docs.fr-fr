---
title: Sqlserverexception, classe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cfcc73705d04b3d3efa7515f74676b0eda120323
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680277"
---
# <a name="sqlserverexception-class"></a>Classe SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une exécution incorrecte ou incomplète d'une instruction SQL.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.sql.SQLException  
  
 **Implémente :** java.io.Serializable  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Notes   
 La classe SQLServerException gère les codes d’état SQL 92 et XOPEN. Il est possible de passer de l'un à l'autre à l'aide d'une propriété de connexion spécifiée par l'utilisateur. Les exceptions sont écrites dans les fichiers journaux ouverts qui ont été spécifiés.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
