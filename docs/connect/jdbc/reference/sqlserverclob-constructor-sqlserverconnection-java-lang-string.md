---
description: Constructeur SQLServerClob (SQLServerConnection, java.lang.String)
title: SQLServerClob, constructeur (SQLServerConnection, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ea4bec9b1d3bc8ab297d548dfb8c94f4007d861
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478593"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>Constructeur SQLServerClob (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md), lorsqu’un objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) et une chaîne de données sont donnés.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la version 2.0 du pilote JDBC. Utilisez plutôt la méthode [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *connection*  
  
 Objet SQLServerConnection.  
  
 *data*  
  
 Données CLOB.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerClob, constructeurs](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
