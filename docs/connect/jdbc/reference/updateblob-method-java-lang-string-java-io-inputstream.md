---
description: Méthode updateBlob (java.lang.String, java.io.InputStream)
title: updateBlob, méthode (java.lang.String, java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 018cd71b-4b58-49a7-990e-d28dbb12da70
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 701fb7df5f8c9632d139357021fb8793551f5147
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462315"
---
# <a name="updateblob-method-javalangstring-javaioinputstream"></a>Méthode updateBlob (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée à l'aide du flux d'entrée spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateBlob(java.lang.String columnLabel,  
                       java.io.InputStream inputStream)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 **String** contenant l’étiquette de colonne.  
  
 *inputStream*  
  
 Objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateBlob est spécifiée par la méthode updateBlob de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateBlob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
