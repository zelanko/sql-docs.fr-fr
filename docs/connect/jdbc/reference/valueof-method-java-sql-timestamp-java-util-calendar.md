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
ms.openlocfilehash: 11d8f8e346fdb0f07770feec815e5aa5fe88355f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68001588"
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
  
 Valeur de décalage.  Les composants de date et d’heure de *calendar* sont définis d’après la valeur *timestamp*.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un objet DateTimeOffset représentant le point dans le temps donné par l’objet java.sql.Timestamp au fuseau horaire de l’objet java.util.Calendar donné.  
  
## <a name="remarks"></a>Notes  
 Cette méthode définit également l’objet java.util.Calendar sur le point dans le temps donné par l’objet java.sql.Timestamp.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
