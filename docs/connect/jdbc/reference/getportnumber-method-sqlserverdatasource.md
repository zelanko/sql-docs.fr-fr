---
title: Méthode getPortNumber (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30b2387b4685440de737ad9e6be7d351ded86506
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736633"
---
# <a name="getportnumber-method-sqlserverdatasource"></a>Méthode getPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le numéro de port actuel utilisé pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur **int** qui contient le numéro de port actuel.  
  
## <a name="remarks"></a>Notes   
 Le numéro de port est le numéro de port TCP/IP utilisé lors de l’ouverture d’une connexion de socket à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété portNumber n'est pas définie, la méthode getPortNumber retourne la valeur par défaut de 1433.  
  
> [!NOTE]  
>  Le [setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md) méthode n’effectue pas de toute vérification de plage sur la valeur de port transmise. Vous pouvez transmettre des numéros qui ne sont pas valides, tels que 99999, sans déclencher d’erreur.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
