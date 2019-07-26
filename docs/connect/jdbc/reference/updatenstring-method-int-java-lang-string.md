---
title: Méthode updateNString (int, Java. lang. String) | Microsoft Docs
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
ms.openlocfilehash: 90aa44eda2af60ffdc73a65e01b3ae12b949d79f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998795"
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
  
 **Entier** qui indique l’index de colonne.  
  
 *nString*  
  
 Objet **String** .  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateNString est spécifiée par la méthode updateNString de l’interface java.sql.ResultSet.  
  
 Cette méthode passe la **chaîne** Java à des colonnes **nchar**, **nvarchar (max)** , **ntext**et **XML** sélectionnées. L'utilisation de cette méthode sur d'autres colonnes de type de données lève une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [updateNString, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
