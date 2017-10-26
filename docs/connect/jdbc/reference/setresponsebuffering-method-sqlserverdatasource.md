---
title: "Méthode setResponseBuffering (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 88cfa89a30461ba3013c7b227651d5d0292c77b2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>Méthode setResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la réponse mise en mémoire tampon pour les connexions créées à l’aide de ce mode de [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *valeur*  
  
 A **chaîne** qui contient le mode de mise en mémoire tampon et de diffusion en continu. Le mode valid peut être une des chaînes de casse suivantes : **complète** ou **adaptive**.  
  
## <a name="remarks"></a>Notes  
 Le **complète** valeur spécifie la lecture de l’ensemble de résultats à partir du serveur en cours d’exécution.  
  
 Le **adaptive** valeur spécifie la mise en mémoire tampon minimale des données lorsque cela est nécessaire. Le **adaptive** valeur est la valeur par défaut en mode de mise en mémoire tampon.  
  
 Pour plus d’informations sur l’utilisation du mode de mise en mémoire tampon de réponse, consultez [à l’aide de mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

