---
title: sp_help (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help
- sp_help_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help
ms.assetid: 913cd5d4-39a3-4a4b-a926-75ed32878884
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fb5e9a1ab72140a08423fa50c10eeb1f2d06ad79
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909084"
---
# <a name="sp_help-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Fournit des informations sur un objet de base de données (n’importe quel objet figurant dans la vue de compatibilité **sys. sysobjects** ), un type de données défini par l’utilisateur ou un type de données.  
  
 
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @objname = ] 'name'` est le nom d’un objet, dans **sysobjects** ou dans un type de données défini par l’utilisateur dans la table **systypes** . *Name* est de type **nvarchar (** 776 **)** , avec NULL comme valeur par défaut. Vous ne pouvez pas spécifier un nom de base de données.  Les noms en deux ou trois parties doivent être délimités, comme 'Personne.TypeAdresse' ou [Personne.TypeAdresse].   
   
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Les jeux de résultats qui sont retournés varient selon que le *nom* est spécifié, le moment où il est spécifié et l’objet de base de données.  
  
1.  Si **sp_help** est exécuté sans argument, les informations récapitulatives des objets de tous les types qui existent dans la base de données active sont retournées.  
  
    |Nom de colonne|Data type|Description|  
    |-----------------|---------------|-----------------|  
    |**Nom**|**nvarchar(** 128 **)**|Nom de l'objet|  
    |**Propriétaire**|**nvarchar(** 128 **)**|Propriétaire de l'objet (il s'agit du principal de la base de données propriétaire de l'objet. Est accordé par défaut au propriétaire du schéma qui contient l'objet.)|  
    |**Object_type**|**nvarchar (** 31 **)**|Type d'objet|  
  
2.  Si le *nom* est un type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un type de données défini par l’utilisateur, **sp_help** retourne ce jeu de résultats.  
  
    |Nom de colonne|Data type|Description|  
    |-----------------|---------------|-----------------|  
    |**Type_name**|**nvarchar(** 128 **)**|Nom du type de données.|  
    |**Storage_type**|**nvarchar(** 128 **)**|Nom de type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
    |**Longueur**|**smallint**|Longueur physique du type de données (en octets).|  
    |**Prec**|**Int**|Précision (nombre total de chiffres).|  
    |**Échelle**|**Int**|Nombre de chiffres à droite du séparateur décimal.|  
    |**Nullable**|**varchar (** 35 **)**|Indique si les valeurs NULL sont autorisées : Oui ou Non.|  
    |**Default_name**|**nvarchar(** 128 **)**|Nom par défaut de ce type de données.<br /><br /> NULL = aucune valeur par défaut n'est liée.|  
    |**Rule_name**|**nvarchar(** 128 **)**|Nom d'une règle associée à ce type.<br /><br /> NULL = aucune valeur par défaut n'est liée.|  
    |**Classement**|**sysname**|Classement du type de données. NULL pour les types de données non caractère.|  
  
3.  Si le *nom* est un objet de base de données autre qu’un type de données, **sp_help** retourne ce jeu de résultats et également d’autres jeux de résultats, en fonction du type d’objet spécifié.  

    |Nom de colonne|Data type|Description|  
    |-----------------|---------------|-----------------|  
    |**Nom**|**nvarchar(** 128 **)**|Nom de table|  
    |**Propriétaire**|**nvarchar(** 128 **)**|Propriétaire de la table|  
    |**Type**|**nvarchar (** 31 **)**|Type de la table|  
    |**Created_datetime**|**datetime**|Date de création de la table|  
  
     Selon l’objet de base de données spécifié, **sp_help** retourne des jeux de résultats supplémentaires.  
  
     Si le *nom* est une table système, une table utilisateur ou une vue, **sp_help** retourne les jeux de résultats suivants. Toutefois, le jeu de résultats qui indique à quel endroit se trouve le fichier de données sur un groupe de fichiers n'est pas retourné pour une vue.  
  
    -   Jeu de résultats supplémentaire retourné sur des objets de colonne :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**Comporte**|**nvarchar(** 128 **)**|Nom de la colonne.|  
        |**Type**|**nvarchar(** 128 **)**|Type de données de la colonne.|  
        |**Calculée**|**varchar (** 35 **)**|Indique si les valeurs de la colonne sont calculées : Oui ou Non.|  
        |**Longueur**|**Int**|Longueur de colonne en octets.<br /><br /> Remarque : si le type de données de la colonne est un type de valeur élevée (**varchar (max)** , **nvarchar (max)** , **varbinary (max)** ou **XML**), la valeur s’affiche comme-1.|  
        |**Prec**|**char (** 5 **)**|Précision de la colonne|  
        |**Échelle**|**char (** 5 **)**|Échelle de la colonne|  
        |**Nullable**|**varchar (** 35 **)**|Indique si les valeurs NULL sont autorisées dans cette colonne : Oui ou Non.|  
        |**TrimTrailingBlanks**|**varchar (** 35 **)**|Élimine les vides. Retourne Oui ou Non.|  
        |**FixedLenNullInSource**|**varchar (** 35 **)**|Pour compatibilité descendante uniquement.|  
        |**Classement**|**sysname**|Classement de la colonne. NULL pour les types de données non caractères.|  
  
    -   Jeu de résultats supplémentaire retourné sur des colonnes d'identité :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**Identity**|**nvarchar(** 128 **)**|Nom de la colonne dont le type de données déclaré est identité.|  
        |**Initiales**|**numeric**|Valeur de départ de la colonne identité.|  
        |**Incrément**|**numeric**|Incrément à appliquer aux valeurs de la colonne.|  
        |**Pas pour la réplication**|**Int**|La propriété IDENTity n’est pas appliquée quand une connexion de réplication, telle que **SQLRepl**, insère des données dans la table :<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   Jeu de résultats supplémentaire retourné sur des colonnes :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|Nom de la colonne d'identification unique.|  
  
    -   Jeu de résultats supplémentaire retourné sur des groupes de fichiers :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar(** 128 **)**|Groupe de fichiers dans lequel se trouvent les données : primaire, secondaire ou journal des transactions.|  
  
    -   Jeu de résultats supplémentaire retourné sur les index :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|Nom de l’index.|  
        |**Index_description**|**varchar (** 210 **)**|Description de l'index.|  
        |**index_keys**|**nvarchar (** 2078 **)**|Noms des colonnes servant de base à l'index. Retourne NULL pour les index columnstores optimisés en mémoire xVelocity.|  
  
    -   Jeu de résultats supplémentaire retourné sur des contraintes :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar (** 146 **)**|Type de contrainte.|  
        |**constraint_name**|**nvarchar(** 128 **)**|Nom de la contrainte.|  
        |**delete_action**|**nvarchar (** 9 **)**|Indique si l'action DELETE est : NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT ou N/A.<br /><br /> Uniquement applicable aux contraintes FOREIGN KEY.|  
        |**update_action**|**nvarchar (** 9 **)**|Indique si l'action UPDATE est : NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT ou N/A.<br /><br /> Uniquement applicable aux contraintes FOREIGN KEY.|  
        |**status_enabled**|**varchar (** 8 **)**|Indique si la contrainte est activée : Enabled, Disabled ou N/A.<br /><br /> Uniquement applicable aux contraintes CHECK et FOREIGN KEY.|  
        |**status_for_replication**|**varchar (** 19 **)**|Indique si la contrainte concerne la réplication.<br /><br /> Uniquement applicable aux contraintes CHECK et FOREIGN KEY.|  
        |**constraint_keys**|**nvarchar (** 2078 **)**|Nom des colonnes qui constituent la contrainte ou, pour les valeurs par défaut ou les règles, le texte qui définit la valeur par défaut ou la règle.|  
  
    -   Jeu de résultats supplémentaire retourné sur des objets de référence :  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**La table est référencée par**|**nvarchar (** 516 **)**|Identifie les autres objets de base de données qui font référence à la table.|  
  
    -   Jeu de résultats supplémentaire retourné sur les procédures stockées, les fonctions ou les procédures stockées étendues.  
  
        |Nom de colonne|Data type|Description|  
        |-----------------|---------------|-----------------|  
        |**Nom_de_paramètre**|**nvarchar(** 128 **)**|Nom du paramètre de la procédure stockée.|  
        |**Type**|**nvarchar(** 128 **)**|Type de données du paramètre de la procédure stockée.|  
        |**Longueur**|**smallint**|Longueur maximale de stockage physique, en octets.|  
        |**Prec**|**Int**|Précision ou nombre total de chiffres.|  
        |**Échelle**|**Int**|Nombre de chiffres situés à droite du séparateur décimal.|  
        |**Param_order**|**smallint**|Ordre du paramètre.|  
  
## <a name="remarks"></a>Notes  
 La procédure **sp_help** recherche un objet dans la base de données active uniquement.  
  
 Si vous ne spécifiez pas *Name* , **sp_help** répertorie les noms d’objets, les propriétaires et les types d’objets pour tous les objets de la base de données active. **sp_helptrigger** fournit des informations sur les déclencheurs.  
  
 **sp_help** expose uniquement les colonnes d’index ordonnées ; par conséquent, il n’expose pas d’informations sur les index XML ou les index spatiaux.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . L’utilisateur doit avoir au moins une autorisation sur *nomobj*. Pour consulter des clés de contrainte, des valeurs par défaut ou des règles de colonne, vous devez disposer de l'autorisation VIEW DEFINITION sur la table.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-information-about-all-objects"></a>A. Retour d'informations sur tous les objets  
 L'exemple suivant fournit des informations sur chaque objet de la base de données `master`.  
  
```  
USE master;  
GO  
EXEC sp_help;  
GO  
```  
  
### <a name="b-returning-information-about-a-single-object"></a>b. Retour d'informations sur un objet unique  
 L'exemple suivant affiche des informations sur la table `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help 'Person.Person';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures &#40;stockées moteur de base de données Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ &#40;Transact-SQL&#41; sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)  
 [sp_helprotect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [ &#40;Transact-SQL&#41; sp_helpuser](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys. sysobjects &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  
