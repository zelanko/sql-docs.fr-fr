---
title: Méthode getSendTimeAsDatetime (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 018d40464d6461cb4182daf5f93139e322517870
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929209"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Méthode getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Retourne le paramètre de la propriété de connexion **sendTimeAsDatetime**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si les valeurs java.sql.Time sont envoyées au serveur en tant que type [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime**. **false** si les valeurs java.sql.Time sont envoyées au serveur en tant que type [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **time**.  
  
## <a name="remarks"></a>Notes  
 Consultez [Définir les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md) pour plus d’informations sur la propriété de connexion **sendTimeAsDatetime**.  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) permet de définir programmatiquement la propriété de connexion **sendTimeAsDatetime**.  
  
 Pour plus d’informations, consultez [Configurer le mode d’envoi des valeurs java.sql.Time au serveur](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
