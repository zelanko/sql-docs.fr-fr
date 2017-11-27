---
title: "Méthode valueOf (java.sql.Timestamp, java.util.Calendar) | Documents Microsoft"
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
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 138a53f22791390600ed21e535a7c26597f46321
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Méthode valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un **DateTimeOffset** objet représentant un point dans le temps d’un décalage particulier à partir de l’heure GMT selon une valeur java.sql.Timestamp et une valeur java.util.Calendar indiquant le décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *timestamp*  
  
 Valeurjava.sql.Timestamp.  
  
 *calendrier*  
  
 Valeur de décalage.  Les composants de date et heure de *calendrier* définira conformément à la *timestamp* valeur.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un objet DateTimeOffset qui représente le point dans le temps spécifié par l’objet java.sql.Timestamp sur fuseau horaire de l’objet java.util.Calendar donné.  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit également l’objet java.util.Calendar au point dans le temps spécifié par l’objet java.sql.Timestamp.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
