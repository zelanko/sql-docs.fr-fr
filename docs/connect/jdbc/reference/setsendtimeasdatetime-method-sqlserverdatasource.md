---
title: Méthode setSendTimeAsDatetime (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 293667d8e3e06fb5eda7a74fdeed58c89fb0f1ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972961"
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Méthode setSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Modifie le paramètre de la propriété de connexion **sendTimeAsDatetime** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sendTimeAsDateTime*  
  
 Valeur booléenne. Quand la valeur true est définie, les valeurs de java.sql.Time sont envoyées au serveur en tant que types [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime**. Quand la valeur false est définie, les valeurs de java.sql.Time sont envoyées au serveur en tant que types [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **time**.  
  
## <a name="remarks"></a>Notes  
 [SQLServerDataSource. getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) retourne le paramètre de la propriété de connexion **sendTimeAsDatetime** .  
  
 Pour plus d’informations sur la propriété de connexion **sendTimeAsDatetime** , consultez [définition des propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Pour plus d’informations, consultez [configuration de la façon dont les valeurs Java. Sql. Time sont envoyées au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
