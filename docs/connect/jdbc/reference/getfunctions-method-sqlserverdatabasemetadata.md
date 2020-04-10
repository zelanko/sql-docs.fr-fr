---
title: Méthode getFunctions (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cafef140d505197bfe1993f65ef17d4cb53e19f5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920331"
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
 *catalog*  
  
 Nom d'un catalogue dans la base de données. Si la chaîne est vide « », le résultat inclut les fonctions sans catalogue. Si elle est **null**, le nom du catalogue n’est pas utilisé pour la recherche.  
  
 *schemaPattern*  
  
 Nom d'un schéma. Si la chaîne est vide « », le résultat inclut les fonctions sans schéma. Si elle est **null**, le nom du schéma n’est pas utilisé pour la recherche.  
  
 *functionNamePattern*  
  
 Nom d'une fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFunctions est spécifiée par la méthode getFunctions de l’interface java.sql.DatabaseMetaData.  
  
 Cette méthode retourne uniquement les fonctions système et utilisateur qui correspondent au nom de schéma et de fonction spécifié.  
  
> [!IMPORTANT]  
>  Le jeu de résultats retourné peut contenir des fonctions que l'utilisateur appelant n'est pas autorisé à exécuter.  
  
 Chaque description de fonction inclut les colonnes suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**Chaîne**|Nom de la base de données qui contient la fonction.|  
|FUNCTION_SCHEM|**Chaîne**|Nom du schéma qui contient la fonction.|  
|FUNCTION_NAME|**Chaîne**|Nom de la fonction.|  
|NUM_INPUT_PARAMS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_OUTPUT_PARAMS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_RESULT_SETS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|Remarques|**Chaîne**|Commentaires sur la fonction.|  
|FUNCTION_TYPE|**short**|Type de la fonction. Ce peut être l’une des valeurs suivantes :<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Toutes les descriptions dans le jeu de résultats retourné sont classées par FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME et SPECIFIC_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
