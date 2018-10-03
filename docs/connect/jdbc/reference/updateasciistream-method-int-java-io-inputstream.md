---
title: updateasciistream, méthode (java.io.InputStream) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 0f8feed0894a21dacc43fb27f5d39fd961093b1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793757"
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
  
 Un **int** qui indique l’index de colonne.  
  
 *x*  
  
 Un objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateAsciiStream est spécifiée par la méthode updateAsciiStream dans l’interface java.sql.ResultSet.  
  
 Cette méthode passe les caractères ASCII (octets) à partir d’un objet InputStream vers des colonnes de caractères convertibles, qui correspondent à la plage ASCII [0x00 – 0x7F] Unicode et aux pages de codes 874, 932, 936, 949, 950 et 1250 jusqu’à 1258. Cette méthode effectue une conversion de la page de classement de destination. La tentative de mise à jour d'une colonne de destination non convertible entraîne la levée d'une exception. Pour les colonnes binaires, des octets bruts sont passés.  
  
 À l’aide de cette méthode pour le **image**, **texte**, et **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données peuvent affecter les performances.  
  
## <a name="see-also"></a> Voir aussi  
 [updateAsciiStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
