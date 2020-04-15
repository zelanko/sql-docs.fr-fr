---
title: Champs descripteur de paramètres évalués par table (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields
ms.assetid: 4e009eff-c156-4d63-abcf-082ddd304de2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7f1f3e26ece880faf1c7f96e674d4f4f161790dd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297794"
---
# <a name="table-valued-parameter-descriptor-fields"></a>Champs de descripteur de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  La prise en charge des paramètres table inclut de nouveaux champs spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les descripteurs de paramètre d'application (APD) ODBC et les descripteurs de paramètre d'implémentation (IPD).  
  
## <a name="remarks"></a>Notes  
  
|Nom|Emplacement|Type|Description|  
|----------|--------------|----------|-----------------|  
|SQL_CA_SS_TYPE_NAME|IPD|SQLTCHAR*|Nom du type de serveur du paramètre table.<br /><br /> Lorsqu’un nom de type paramètre de valeur de table est spécifié lors d’un appel à SQLBindParameter, il doit toujours être spécifié comme une valeur Unicode, même dans les applications qui sont construites sous forme d’applications ANSI. La valeur utilisée pour le paramètre *StrLen_or_IndPtr* doit être soit SQL_NTS ou la longueur de la chaîne du nom multiplié par sizeof (WCHAR).<br /><br /> Lorsqu’un nom de type de paramètre de valeur de table est spécifié via SQLSetDescField, il peut être spécifié en utilisant un littéral conforme à la façon dont l’application est construite. Le Gestionnaire de pilotes ODBC effectuera toute conversion Unicode requise.|  
|SQL_CA_SS_TYPE_CATALOG_NAME (lecture seule)|IPD|SQLTCHAR*|Catalogue où le type est défini.|  
|SQL_CA_SS_TYPE_SCHEMA_NAME|IPD|SQLTCHAR*|Schéma où le type est défini.|  
  
 Les applications ne doivent pas définir SQL_CA_SS_TYPE_CATALOG_NAME pour les paramètres table. Si tel est le cas, SQL_ERROR est retourné et un enregistrement de diagnostic est journalisé avec SQLSTATE = HY091 et le message « Identificateur de champ de descripteur non valide ».  
  
 Les attributs d'instruction et les champs d'en-tête de descripteur suivants s'appliquent aux paramètres table lorsque le focus de paramètre est défini sur un paramètre table :  
  
|Nom|Emplacement|Type|Description|  
|----------|--------------|----------|-----------------|  
|SQL_ATTR_PARAMSET_SIZE<br /><br /> (Équivaut à SQL_DESC_ARRAY_SIZE dans le descripteur APD.)|APD|SQLUINTEGER|Taille du tableau de mémoires tampon pour un paramètre table. Il s'agit du nombre maximal de lignes que les mémoires tampon peuvent prendre en charge ou de la taille des mémoires tampon dans les lignes ; la valeur du paramètre table peut elle-même avoir un nombre de lignes supérieur ou inférieur à la capacité des mémoires tampon. 1 constitue la valeur par défaut.<br /><br /> Remarque : Si SQL_SOPT_SS_PARAM_FOCUS est réglée à sa valeur par défaut de 0, SQL_ATTR_PARAMSET_SIZE se réfère à l’instruction et spécifie le nombre de paramètres. Si SQL_SOPT_SS_PARAM_FOCUS est pour valeur l'ordinal d'un paramètre table, il fait référence au paramètre table et spécifie le nombre de lignes par jeu de paramètres pour le paramètre table.|  
|SQL_ATTR_PARAM _BIND_TYPE|APD|SQLINTEGER|La valeur par défaut est SQL_PARAM_BIND_BY_COLUMN.<br /><br /> Pour sélectionner la liaison selon les lignes, ce champ a pour valeur la longueur de la structure ou une instance d'une mémoire tampon qui sera liée à un jeu de lignes de paramètre table. Cette durée doit inclure l'espace pour toutes les colonnes dépendantes et tout remplissage de la structure ou de la mémoire tampon. Cela garantit que lorsque l'adresse d'une colonne dépendante est incrémentée de la longueur spécifiée, le résultat pointera vers le début de la même colonne dans la ligne suivante. Lors de **l’utilisation de la taille de l’opérateur** dans ANSI C, ce comportement est garanti.|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|APD|SQLINTEGER*|La valeur par défaut est un pointeur null.<br /><br /> Si ce champ n'est pas NULL, le pilote déréférence le pointeur, ajoute la valeur déréférencée à chacun des champs différés dans l'enregistrement de descripteur (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR) et utilise les nouvelles valeurs de pointeur pour accéder aux valeurs de données.|  
  
 Ces champs sont uniquement valides avec des paramètres table et sont ignorés pour d'autres types de données.  
  
 SQL_CA_SS_TYPE_NAME est facultatif pour les appels de procédure stockée. Il doit être spécifié pour les instructions SQL qui ne sont pas des appels de procédure pour permettre au serveur de déterminer le type du paramètre table.  
  
 Si le nom de type est reqired et que le type de table pour le paramètre table est défini dans un schéma différent de la procédure stockée, SQL_CA_SS_TYPE_SCHEMA_NAME doit être spécifié dans le descripteur de paramètre d'implémentation (IPD). Sinon, le serveur ne pourra pas déterminer le type du paramètre table Cela se traduira par une erreur lorsque vous appelez SQLExecute ou SQLExecDirect. L'erreur indiquera SQLSTATE = 07006 et le message « Violation de l'attribut de type de données restreint ».  
  
 Les colonnes de paramètre table peuvent utiliser la liaison selon les lignes ou selon les colonnes. La valeur par défaut est la liaison selon les colonnes. La liaison selon les lignes peut être spécifiée en définissant SQL_ATTR_PARAM_BIND_TYPE et SQL_ATTR_PARAM_BIND_OFFSET_PTR. Cela équivaut à la liaison selon les lignes de colonnes et de paramètres.  
  
 SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME peuvent également être utilisés pour récupérer le catalogue et le schéma associés aux paramètres du type CLR défini par l'utilisateur. Ils constituent des alternatives aux attributs existants de schéma de catalogue spécifiques au type pour ces types.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
