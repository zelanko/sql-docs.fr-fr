---
title: Méthode setSendStringParametersAsUnicode (SQLServerDataSource) | Documents Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18a2f401fb19d1ac90cc5fb1f7f685c03f02919a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>Méthode setSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit un **booléenne** valeur qui indique si l’envoi de paramètres de chaîne au serveur au format UNICODE est activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sendStringParametersAsUnicode*  
  
 **true** si les paramètres de chaîne sont envoyés au serveur au format UNICODE. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété sendStringParametersAsUnicode a la valeur **true**, qui est la valeur par défaut, les paramètres de chaîne sont envoyés au serveur au format UNICODE. Si sendStringParametersAsUnicode a la valeur **false** paramètres string sont envoyés au serveur dans un format ASCII/MBCS, pas au format UNICODE. Si sendStringParametersAsUnicode n’est pas définie, [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) retourne la valeur par défaut de **true**.  
  
 Pour plus d’informations sur la propriété de connexion sendStringParametersAsUnicode, consultez [définissant les propriétés de connexion](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
