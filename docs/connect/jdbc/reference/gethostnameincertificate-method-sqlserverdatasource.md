---
title: Méthode getHostNameInCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- getHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 45ea04e2-9ea5-4171-9136-d09f8a95e128
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67978d2597a5167d3930c85ee453dc6d985f021e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67982898"
---
# <a name="gethostnameincertificate-method-sqlserverdatasource"></a>Méthode getHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom d'hôte utilisé dans la validation du certificat SSL (Secure Sockets Layer) SQL Server.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant le nom d’hôte ou Null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Le nom d'hôte sert à valider la valeur du certificat SSL SQL Server lorsque la couche de communication est chiffrée à l'aide du protocole SSL.  
  
 Si le nom d’hôte n’est pas défini, la méthode [getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md) retourne la valeur Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
