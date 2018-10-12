---
title: updateNClob, méthode (java.lang.String, java.sql.NClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a025d124-3634-49fa-8bb5-e9b98f2d5de3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dca56a83f46664c8a4f059c37210122c798faf50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667977"
---
# <a name="updatenclob-method-javalangstring-javasqlnclob"></a>Méthode updateNClob (java.lang.String, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur **NClob**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.sql.NClob x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 Un **chaîne** qui indique l’étiquette de colonne.  
  
 *x*  
  
 Un objet NClob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateNClob est spécifiée par la méthode updateNClob dans l’interface java.sql.ResultSet.  
  
 Cette méthode est prise en charge uniquement sur **nvarchar (max)**, **ntext**, et **xml** colonnes. L'utilisation de cette méthode sur n'importe quel autre type de données entraîne la levée d'une exception.  
  
## <a name="see-also"></a> Voir aussi  
 [updateNClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
