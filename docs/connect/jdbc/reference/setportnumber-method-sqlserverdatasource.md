---
title: Méthode setPortNumber (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15e0ff764637869428945ab3eb4b6c44b055b436
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728197"
---
# <a name="setportnumber-method-sqlserverdatasource"></a>Méthode setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le numéro de port à utiliser pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *portNumber*  
  
 Valeur **int** qui contient le numéro de port.  
  
## <a name="remarks"></a>Notes   
 Le numéro de port est le numéro de port TCP/IP utilisé lors de l’ouverture d’une connexion de socket à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété portNumber n’est pas définie, la méthode [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) retourne la valeur par défaut, 1433.  
  
> [!NOTE]  
>  La méthode setPortNumber n’effectue pas toute vérification de plage sur la valeur de port transmise. Vous pouvez transmettre un numéro de port qui n’est pas valide, comme 99999, sans déclencher d’erreur.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
