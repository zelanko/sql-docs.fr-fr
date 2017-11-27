---
title: "Méthode getFunctions (SQLServerDatabaseMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d09162647b6d5a4076bb60b3bf05e1e90eb27dee
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>Méthode getFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des fonctions système et utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalogue*  
  
 Nom d'un catalogue dans la base de données. Si la chaîne est vide « », le résultat inclut les fonctions sans catalogue. S’il s’agit **null**, le nom du catalogue n’est pas utilisé pour la recherche.  
  
 *schemaPattern*  
  
 Nom d'un schéma. Si la chaîne est vide « », le résultat inclut les fonctions sans schéma. S’il s’agit **null**, le nom de schéma n’est pas utilisé pour la recherche.  
  
 *functionNamePattern*  
  
 Nom d'une fonction.  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFunctions est spécifiée par la méthode getFunctions dans l’interface java.sql.DatabaseMetaData.  
  
 Cette méthode retourne uniquement les fonctions système et utilisateur qui correspondent au nom de schéma et de fonction spécifié.  
  
> [!IMPORTANT]  
>  Le jeu de résultats retourné peut contenir des fonctions que l'utilisateur appelant n'est pas autorisé à exécuter.  
  
 Chaque description de fonction inclut les colonnes suivantes :  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**Chaîne**|Nom de la base de données qui contient la fonction.|  
|FUNCTION_SCHEM|**Chaîne**|Nom du schéma qui contient la fonction.|  
|FUNCTION_NAME|**Chaîne**|Nom de la fonction.|  
|NUM_INPUT_PARAMS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_OUTPUT_PARAMS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_RESULT_SETS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|REMARKS|**Chaîne**|Commentaires sur la fonction.|  
|FUNCTION_TYPE|**courte**|Type de la fonction. Il peut prendre l’une des valeurs suivantes :<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Toutes les descriptions dans le jeu de résultats retourné sont classées par FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME et SPECIFIC_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
