---
title: Méthode updateNClob (int, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 17adafd4-3ac3-4ff0-af9d-f087cc5ef936
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5bf40ccd10d1c97728feadbb8a3d1c5512df070
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612117"
---
# <a name="updatenclob-method-int-javaioreader"></a>Méthode updateNClob (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec l’objet **Reader** spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
 *reader*  
  
 Un objet de lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateNClob est spécifiée par la méthode updateNClob dans l’interface java.sql.ResultSet.  
  
 Cette méthode est prise en charge uniquement sur **nvarchar (max)**, **ntext**, et **xml** colonnes. L'utilisation de cette méthode sur n'importe quel autre type de données entraîne la levée d'une exception.  
  
## <a name="see-also"></a> Voir aussi  
 [updateNClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
