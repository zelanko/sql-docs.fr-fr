---
title: Méthode updateAsciiStream (java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1dcc3d4f-ae30-45c0-afad-a531358807af
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9acd8b75a7152a8e10faeb7f80d6d02c070ad2f0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67985525"
---
# <a name="updateasciistream-method-int-javaioinputstream"></a>Méthode updateAsciiStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur de flux ASCII.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateAsciiStream(int columnIndex,  
                              java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 **int** indiquant l’index de la colonne.  
  
 *x*  
  
 Objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateAsciiStream est spécifiée par la méthode updateAsciiStream de l’interface java.sql.ResultSet.  
  
 Cette méthode passe les caractères ASCII (octets) à partir d’un objet InputStream vers des colonnes de caractères convertibles, qui correspondent à la plage ASCII [0x00 - 0x7F] Unicode et aux pages de codes 874, 932, 936, 949, 950 et 1250 jusqu’à 1258. Cette méthode effectue une conversion de la page de classement de destination. La tentative de mise à jour d'une colonne de destination non convertible entraîne la levée d'une exception. Pour les colonnes binaires, des octets bruts sont passés.  
  
 Utilisée sur les types de données **image**, **text** et **ntext**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode risque d’avoir un effet sur les performances.  
  
## <a name="see-also"></a> Voir aussi  
 [updateAsciiStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
