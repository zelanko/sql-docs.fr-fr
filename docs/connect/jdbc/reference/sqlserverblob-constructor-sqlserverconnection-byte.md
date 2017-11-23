---
title: Constructeur SQLServerBlob (SQLServerConnection, byte) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection, byte[].SQLServerBlob
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b75ad63c8bbf1a928c8a464b3997713f4a6e582e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>Constructeur SQLServerBlob (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md) classe en fonction d’un [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objet et un **octets** tableau.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la version 2.0 du pilote JDBC. Au lieu de cela, utilisez le [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md) méthode de la [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *connexion*  
  
 Un objet SQLServerConnection.  
  
 *données*  
  
 A **octets** tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [Constructeurs SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [Membres de SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
