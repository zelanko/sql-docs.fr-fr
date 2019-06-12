---
title: updatenstring, méthode (int, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1bb909f1-4a96-4be1-adea-36c8d9703112
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c00621a2fedce7d9fba4d65f248b412627ee6233
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776654"
---
# <a name="updatenstring-method-int-javalangstring"></a>Méthode updateNString (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur **String** suivant l’index de colonne spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateNString(int columnIndex,  
                        java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
 *nString*  
  
 Un **chaîne** objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateNString est spécifiée par la méthode updateNString dans l’interface java.sql.ResultSet.  
  
 Cette méthode passe Java **chaîne** à la sélection **nchar**, **nvarchar (max)** , **ntext**, et **xml** colonnes. L'utilisation de cette méthode sur d'autres colonnes de type de données lève une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [updateNString, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
