---
title: "Méthode getResponseBuffering (SQLServerDataSource) | Documents Microsoft"
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
apiname: SQLServerDataSource.getResponseBuffering()
apilocation: SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
caps.latest.revision: "27"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b11609d9b29bbd76a65c3db3dff12a94d4d96767
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>Méthode getResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la réponse mise en mémoire tampon de mode pour cette [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient une minuscule **complète** ou **adaptive**.  
  
## <a name="remarks"></a>Notes  
 Le **complète** valeur spécifie la lecture de l’ensemble de résultats à partir du serveur en cours d’exécution.  
  
 Le **adaptive** valeur spécifie la mise en mémoire tampon minimale des données lorsque cela est nécessaire. Le **adaptive** valeur est la valeur par défaut en mode de mise en mémoire tampon.  
  
 Pour plus d’informations sur l’utilisation du mode de mise en mémoire tampon de réponse, consultez [à l’aide de mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setResponseBuffering &#40; SQLServerDataSource &#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
