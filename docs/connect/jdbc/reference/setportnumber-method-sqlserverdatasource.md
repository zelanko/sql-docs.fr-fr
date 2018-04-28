---
title: Méthode setPortNumber (SQLServerDataSource) | Documents Microsoft
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
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 777493f356306fcb2adad1a1066795246e5a71ff
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setportnumber-method-sqlserverdatasource"></a>Méthode setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le numéro de port à utiliser pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numéro de port*  
  
 Un **int** valeur qui contient le numéro de port.  
  
## <a name="remarks"></a>Notes  
 Le numéro de port est le numéro de port TCP/IP utilisé lors de l’ouverture d’une connexion de socket à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Si la propriété portNumber n’est pas définie, la [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) méthode retourne la valeur par défaut 1433.  
  
> [!NOTE]  
>  La méthode setPortNumber n’effectue aucune vérification sur la valeur de port transmise de plage. Vous pouvez passer un numéro de port qui n’est pas valide, comme 99999, sans déclencher d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
