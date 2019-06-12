---
title: Méthode getFunctionColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cd4958db78e2e35d29bcc47428295db50f7e5678
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774631"
---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>Méthode getFunctionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des paramètres de fonctions système ou utilisateur du catalogue spécifié et un type de retour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 Un **chaîne** qui contient le nom du catalogue. Si la chaîne est vide « », le résultat inclut les fonctions sans catalogue. Si elle est **null**, le nom du catalogue n’est pas utilisé pour la recherche.  
  
 *schemaPattern*  
  
 **Chaîne** contenant le modèle de nom du schéma. Si la chaîne est vide « », le résultat inclut les fonctions sans schéma. Si elle est **null**, le nom du schéma n’est pas utilisé pour la recherche.  
  
 *functionNamePattern*  
  
 **Chaîne** qui contient le nom d’une fonction.  
  
 *columnNamePattern*  
  
 **Chaîne** qui contient le nom d’un paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumns est spécifiée par la méthode getColumns de l’interface java.sql.DatabaseMetaData.  
  
 Cette méthode retourne uniquement les fonctions et paramètres qui correspondent au nom de schéma, de fonction et de paramètre spécifié avec le catalogue spécifié.  
  
 Chaque ligne du jeu de résultats inclut les colonnes suivantes pour une description de paramètre, une description de colonne ou un type de retour :  
  
|Créer une vue d’abonnement|Type|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Nom de la base de données qui contient la fonction.|  
|FUNCTION_SCHEM|**String**|Schéma pour la fonction.|  
|FUNCTION_NAME|**String**|Nom de la fonction.|  
|COLUMN_NAME|**String**|Nom d'un paramètre ou d'une colonne.|  
|COLUMN_TYPE|**short**|**Type de la colonne. Il peut avoir une des valeurs suivantes :**<br /><br /> functionColumnUnknown (0) : type inconnu.<br /><br /> functionColumnIn (1) : paramètre d'entrée.<br /><br /> functionColumnInOut (2) : paramètre d'entrée/sortie.<br /><br /> functionColumnOut (3) : paramètre de sortie.<br /><br /> functionReturn (4) : valeur de retour de fonction.<br /><br /> functionColumnResult (5) : un paramètre ou une colonne est une colonne dans le jeu de résultats.|  
|DATA_TYPE|**smallint**|Type de données SQL de Java.sql.Types.|  
|TYPE_NAME|**String**|Nom du type de données.|  
|PRECISION|**Int**|Nombre total de chiffres significatifs.|  
|LENGTH|**Int**|La longueur des données en octets.|  
|SCALE|**short**|Nombre de chiffres à droite de la virgule décimale.|  
|RADIX|**short**|Base des types numériques.|  
|NULLABLE|**short**|Indique si le paramètre ou la valeur de retour peut contenir une valeur **null**.<br /><br /> **Il peut avoir une des valeurs suivantes :**<br /><br /> functionNoNulls (0) : la valeur NULL n'est pas autorisée.<br /><br /> functionNullable (1) : la valeur NULL est autorisée.<br /><br /> functionNullableUnknown (2) : inconnue.|  
|REMARKS|**String**|Commentaires sur une colonne ou un paramètre.|  
|COLUMN_DEF|**String**|Valeur par défaut de la colonne.<br /><br /> **Remarque :** Ces informations sont disponibles avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et sont spécifiques au pilote JDBC.|  
|SQL_DATA_TYPE|**smallint**|Cette colonne est la même que la colonne **DATA_TYPE**, excepté pour les types de données **datetime** et **interval** ISO.<br /><br /> **Remarque :** Ces informations sont disponibles avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et sont spécifiques au pilote JDBC.|  
|SQL_DATETIME_SUB|**smallint**|Le sous-code **interval** ISO de **datetime** si la valeur de **SQL_DATA_TYPE** est **SQL_DATETIME** ou **SQL_INTERVAL**. Pour les données de types autres que **datetime** et ISO **intervalle**, cette colonne est NULL.<br /><br /> **Remarque :** Ces informations sont disponibles avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et sont spécifiques au pilote JDBC.|  
|CHAR_OCTET_LENGTH|**Int**|Longueur maximale des paramètres ou colonnes binaires et basés sur des caractères. Pour les autres types de données, il s'agit de la valeur NULL.|  
|ORDINAL_POSITION|**Int**|Pour les paramètres d'entrée et de sortie, elle représente la position commençant à 1.<br /><br /> Pour les colonnes de jeux de résultats, il s'agit de la position de la colonne dans le jeu de résultats commençant à 1.<br /><br /> Pour la valeur de retour, il s'agit de la valeur 0.|  
|IS_NULLABLE|**String**|Détermine l'acceptation des valeurs NULL par un paramètre ou une colonne.<br /><br /> Il peut avoir une des valeurs suivantes :<br /><br /> **Oui**: le paramètre ou une colonne peut inclure des valeurs NULL.<br /><br /> **NE**: le paramètre ou une colonne ne peut pas inclure des valeurs NULL.<br /><br /> Chaîne vide (« ») : inconnue.|  
|SS_TYPE_CATALOG_NAME|**String**|Nom du catalogue qui contient le type défini par l'utilisateur (UDT).|  
|SS_TYPE_SCHEMA_NAME|**String**|Nom du schéma qui contient le type défini par l'utilisateur (UDT).|  
|SS_UDT_CATALOG_NAME|**String**|Type défini par l'utilisateur (UDT) du nom complet.|  
|SS_UDT_SCHEMA_NAME|**String**|Nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, la chaîne est vide.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Nom d'une collection de schémas XML. Si le nom est introuvable, la chaîne est vide.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Nom du catalogue qui contient le type défini par l'utilisateur (UDT).|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Nom du schéma qui contient le type défini par l'utilisateur (UDT).|  
|SS_DATA_TYPE|**tinyint**|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisé par les procédures stockées étendues.<br /><br /> **Remarque** : Pour plus d’informations sur les types de données retournés par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez la rubrique « Types de données (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
