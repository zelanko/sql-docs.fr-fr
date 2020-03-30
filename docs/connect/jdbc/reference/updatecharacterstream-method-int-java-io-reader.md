---
title: updateCharacterStream, méthode (int, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4dddf885-0482-4776-8e9a-69f6c6270931
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b08a6574f16159e5eebb9a95af7483b2ce7b0c84
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67996759"
---
# <a name="updatecharacterstream-method-int-javaioreader"></a>Méthode updateCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur de flux de caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateCharacterStream(int columnIndex,  
                                  java.io.Reader x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 **int** indiquant l’index de la colonne.  
  
 *x*  
  
 Objet Reader.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateCharacterStream est spécifiée par la méthode updateCharacterStream de l’interface java.sql.ResultSet.  
  
 Cette méthode passe les caractères Unicode à partir d’un objet Reader à des colonnes de texte et binaires sélectionnées. Cela inclut toutes les colonnes de texte et les colonnes **binary**, **varbinary**, **varbinary(max)** , **image** et **xml**, mais pas les colonnes **udt**.  
  
 Utilisée sur les types de données **image**, **text** et **ntext**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode risque d’avoir un effet sur les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [updateCharacterStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
