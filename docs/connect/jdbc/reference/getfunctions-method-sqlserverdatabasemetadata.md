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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fe24a26956a295ccfd00f8d782611057cf019308
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774617"
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
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumns est spécifiée par la méthode getColumns de l’interface java.sql.DatabaseMetaData.  
  
 Cette méthode retourne uniquement les fonctions système et utilisateur qui correspondent au nom de schéma et de fonction spécifié.  
  
> [!IMPORTANT]  
>  Le jeu de résultats retourné peut contenir des fonctions que l'utilisateur appelant n'est pas autorisé à exécuter.  
  
 Chaque description de fonction inclut les colonnes suivantes :  
  
|Créer une vue d’abonnement|Type|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Nom de la base de données qui contient la fonction.|  
|FUNCTION_SCHEM|**String**|Nom du schéma qui contient la fonction.|  
|FUNCTION_NAME|**String**|Nom de la fonction.|  
|NUM_INPUT_PARAMS|**Int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_OUTPUT_PARAMS|**Int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_RESULT_SETS|**Int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|REMARKS|**String**|Commentaires sur la fonction.|  
|FUNCTION_TYPE|**short**|Type de la fonction. Il peut avoir une des valeurs suivantes :<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Toutes les descriptions dans le jeu de résultats retourné sont classées par FUNCTION_CAT, FUNCTION_SCHEM, FUNCTION_NAME et SPECIFIC_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
