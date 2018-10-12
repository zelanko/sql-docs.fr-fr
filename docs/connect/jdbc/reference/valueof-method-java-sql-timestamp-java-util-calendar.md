---
title: valueOf, méthode (java.sql.Timestamp, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd94495081d99521758747f174268d2163cf67e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742737"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Méthode valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet **DateTimeOffset** représentant un point précis dans le temps pour un décalage en particulier par rapport à l’heure GMT en fonction d’une valeur java.sql.Timestamp et d’une valeur java.util.Calendar indiquant le décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *timestamp*  
  
 Valeurjava.sql.Timestamp.  
  
 *calendar*  
  
 Valeur de décalage.  Les composants de date et heure de *calendrier* définira conformément à la *timestamp* valeur.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un objet DateTimeOffset qui représente le point dans le temps indiqué par l’objet java.sql.Timestamp au fuseau horaire de l’objet java.util.Calendar donné.  
  
## <a name="remarks"></a>Notes   
 Cette méthode définit également l’objet java.util.Calendar au point dans le temps indiqué par l’objet java.sql.Timestamp.  
  
## <a name="see-also"></a> Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
