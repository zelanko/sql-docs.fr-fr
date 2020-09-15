---
description: Méthode valueOf (java.sql.Timestamp, java.util.Calendar)
title: valueOf, méthode (java.sql.Timestamp, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6046069a5e2e93cf2d14d0ec999670054348765a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88396115"
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
 [Membres de DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
