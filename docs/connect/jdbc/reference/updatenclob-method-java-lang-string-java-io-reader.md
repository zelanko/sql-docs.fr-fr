---
title: updateNClob, méthode (java.lang.String, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 87621ca7-e64a-49e2-b9c2-551390adaa26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 429ff64469bb904a3cc8de65f518b0e5fa72abad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998618"
---
# <a name="updatenclob-method-javalangstring-javaioreader"></a>Méthode updateNClob (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée à l’aide de l’objet Reader spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 **Chaîne** qui indique l’étiquette de colonne.  
  
 *reader*  
  
 Objet lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNClob est spécifiée par la méthode getNClob de l’interface java.sql.ResultSet.  
  
 Cette méthode est prise en charge uniquement sur les colonnes **nvarchar (max)** , **ntext**et **XML** . L'utilisation de cette méthode sur n'importe quel autre type de données entraîne la levée d'une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [updateNClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
