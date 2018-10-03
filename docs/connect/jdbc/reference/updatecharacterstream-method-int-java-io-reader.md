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
manager: craigg
ms.openlocfilehash: be9761b346eaa2e29bbffb12cb79ec2da13316b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798807"
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
  
 Un **int** qui indique l’index de colonne.  
  
 *x*  
  
 Un objet de lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateCharacterStream est spécifiée par la méthode updateCharacterStream dans l’interface java.sql.ResultSet.  
  
 Cette méthode passe les caractères Unicode à partir d’un objet Reader à des colonnes de texte et binaires sélectionnées. Cela inclut toutes les colonnes de texte et les colonnes **binary**, **varbinary**, **varbinary(max)**, **image** et **xml**, mais pas les colonnes **udt**.  
  
 À l’aide de cette méthode pour le **image**, **texte**, et **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données peuvent affecter les performances.  
  
## <a name="see-also"></a> Voir aussi  
 [updateCharacterStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
