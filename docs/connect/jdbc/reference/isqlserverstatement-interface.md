---
title: ISQLServerStatement, Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7f83b514-6e76-4f37-baf3-a10db2010e7c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7a49ef95ac7e6ee122252577ccff9ec535c912fe
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796421"
---
# <a name="isqlserverstatement-interface"></a>Interface ISQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente l'implémentation de base de la fonctionnalité d'instruction JDBC. Cette interface a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.sql.Statement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public interface ISQLServerStatement  
```  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée par [classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 Cette interface expose les méthodes spécifiques au [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] suivantes :  
  
|Méthode|Pour plus d'informations, consultez|  
|------------|-------------------------------|  
|public String getResponseBuffering|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|  
|public void setResponseBuffering|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
