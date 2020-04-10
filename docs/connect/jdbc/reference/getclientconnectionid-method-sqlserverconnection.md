---
title: getClientConnectionID Method (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 461a3a0e217fb2ad973830eaffc86ff048830b83
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907594"
---
# <a name="getclientconnectionid-method-sqlserverconnection"></a>getClientConnectionID, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient l'ID de la tentative de connexion la plus récente, que cette tentative ait réussi ou non.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
public Java.util.UUID SQLServerConnection.getClientConnectionID();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 GUID de 16 octets représentant l'ID de connexion de la dernière tentative de connexion. Ou NULL, s'il y a un échec après le lancement de la demande de connexion et après la négociation de préconnexion.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur l’accès aux informations de diagnostic dans le journal des événements étendus, consultez [Accès aux informations de diagnostic dans le journal des événements étendus](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 L'exemple suivant montre comment obtenir l'ID de connexion :  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 L'exemple suivant montre une autre façon d'obtenir l'ID de connexion :  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("...");  
ds.setPassword("...");  
ds.setServerName("...");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 **getClientConnectionID** fonctionne quelle que soit la version du serveur auquel vous vous connectez, mais les journaux des événements étendus et l’entrée des erreurs de tampon en anneau de connectivité ne seront pas présents dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2008 R2 et les versions antérieures.  
  
 Vous pouvez également localiser l'ID de connexion dans le journal des événements étendus si l'échec concerne le serveur et si l'événement étendu permet l'enregistrement de l'ID de connexion. Vous pouvez également trouver l’ID de connexion dans la mémoire tampon de l’anneau de connectivité ([Résolution des problèmes de connectivité dans SQL Server 2008 avec la mémoire tampon de l’anneau de connectivité](https://go.microsoft.com/fwlink/?LinkId=207752)) pour certaines erreurs de connexion. Si l'ID de connexion n'est pas dans la mémoire tampon de l'anneau de connexion, vous pouvez supposer qu'il s'agit d'une erreur réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
