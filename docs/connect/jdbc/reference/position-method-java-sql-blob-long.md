---
title: "Méthode position (java.sql.Blob, long) | Documents Microsoft"
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
- SQLServerBlob.position (java.sql.Blob.long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebd005e5-f6c5-4789-87f9-d2fdacd35060
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7c3f740409e7a8d7a5cbc8989ae8aa074703305
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="position-method-javasqlblob-long"></a>Méthode position (java.sql.Blob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la position d'un modèle spécifié dans le BLOB, en fonction du modèle fourni et de l'index de départ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public long position(java.sql.Blob pattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *modèle*  
  
 Le modèle à rechercher.  
  
 *Démarrer*  
  
 Index de départ pour la recherche.  
  
## <a name="return-value"></a>Valeur retournée  
 A **long** valeur de la position où le modèle a été trouvé, ou -1 si elle est introuvable.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Position de cette méthode est spécifiée par la méthode de position dans l’interface java.sql.Blob.  
  
## <a name="see-also"></a>Voir aussi  
 [Placez la méthode &#40; SQLServerBlob &#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [Méthodes SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membres de SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  

