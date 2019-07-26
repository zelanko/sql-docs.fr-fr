---
title: Méthode getUDTs (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getUDTs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4396453-dcb0-4132-8325-06b3c7896b3b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f51e5345cf7c7b78a0a3a37220927000af7d0fa7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978422"
---
# <a name="getudts-method-sqlserverdatabasemetadata"></a>Méthode getUDTs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des types définis par l'utilisateur dans un schéma particulier.  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge avec [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Lorsqu'elle est utilisée, cette méthode retourne toujours un jeu de résultats vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getUDTs(java.lang.String catalog,  
                                  java.lang.String schemaPattern,  
                                  java.lang.String typeNamePattern,  
                                  int[] types)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 **Chaîne** qui contient le nom du catalogue.  
  
 *schemaPattern*  
  
 **Chaîne** contenant le modèle de nom du schéma.  
  
 *typeNamePattern*  
  
 **String** contenant le modèle du nom de type.  
  
 *types*  
  
 Tableau de int qui contient les types de données à inclure. Null indique que tous les types doivent être inclus.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getUDTs est spécifiée par la méthode getUDTs de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
