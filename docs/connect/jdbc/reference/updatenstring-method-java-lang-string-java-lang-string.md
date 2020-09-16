---
description: Méthode updateNString (java.lang.String, java.lang.String)
title: updateNString, méthode (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6daca03f-c60f-4842-b9e3-11d136e78312
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 21edbf36ab5817f02bcf049654bc083d2cd7624a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450107"
---
# <a name="updatenstring-method-javalangstring-javalangstring"></a>Méthode updateNString (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur **String** à l’aide de l’étiquette de colonne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateNString(java.lang.String columnLabel,  
                          java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 **String** contenant l’étiquette de colonne.  
  
 *nString*  
  
 Objet **String**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateNString est spécifiée par la méthode updateNString de l’interface java.sql.ResultSet.  
  
 Cette méthode transmet une **String** Java aux colonnes **nchar**, **nvarchar(max)**, **ntext** et **xml** sélectionnées. L'utilisation de cette méthode sur d'autres colonnes de type de données lève une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [updateNString, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
