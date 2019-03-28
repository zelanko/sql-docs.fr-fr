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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f5e514307e1427cea0ea1bb4d75e7bf0806fd516
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537111"
---
# <a name="sphelp-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Fournit des informations sur un objet de base de données (tout objet répertorié dans le **sys.sysobjects** affichage de compatibilité), un type de données défini par l’utilisateur ou un type de données.  
  
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @objname = ] 'name'` Est le nom de n’importe quel objet, dans **sysobjects** ou type de toutes les données définies par l’utilisateur dans le **systypes** table. *nom* est **nvarchar (** 776 **)**, avec NULL comme valeur par défaut. Vous ne pouvez pas spécifier un nom de base de données.  Les noms en deux ou trois parties doivent être délimités, comme 'Personne.TypeAdresse' ou [Personne.TypeAdresse].   
   
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Les jeux de résultats qui sont retournées varient selon que *nom* est spécifié, lorsqu’il est spécifié, et quel objet de base de données, il est.  
  
1.  Si **sp_help** est exécuté sans arguments, les informations récapitulatives sur les objets de tous les types qui existent dans la base de données actuelle est retournée.  
  
    |Nom de colonne|Type de données|Description|  
    |-----------------|---------------|-----------------|  
    |**Nom**|**nvarchar(** 128 **)**|Nom de l'objet|  
    |**Propriétaire**|**nvarchar(** 128 **)**|Propriétaire de l'objet (il s'agit du principal de la base de données propriétaire de l'objet. Est accordé par défaut au propriétaire du schéma qui contient l'objet.)|  
    |**Object_type**|**nvarchar(** 31 **)**|Type d'objet|  
  
2.  Si *nom* est un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données ou le type de données défini par l’utilisateur, **sp_help** retourne ce jeu de résultats.  
  
    |Nom de colonne|Type de données|Description|  
    |-----------------|---------------|-----------------|  
    |**Type_name**|**nvarchar(** 128 **)**|Nom du type de données.|  
    |**Storage_type**|**nvarchar(** 128 **)**|Nom de type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
    |**Longueur**|**smallint**|Longueur physique du type de données (en octets).|  
    |**PREC**|**Int**|Précision (nombre total de chiffres).|  
    |**Échelle**|**Int**|Nombre de chiffres à droite du séparateur décimal.|  
    |**Nullable**|**varchar(** 35 **)**|Indique si les valeurs NULL sont autorisées : Oui ou Non.|  
    |**Default_name**|**nvarchar(** 128 **)**|Nom par défaut de ce type de données.<br /><br /> NULL = aucune valeur par défaut n'est liée.|  
    |**Nom_règle**|**nvarchar(** 128 **)**|Nom d'une règle associée à ce type.<br /><br /> NULL = aucune valeur par défaut n'est liée.|  
    |**Classement**|**sysname**|Classement du type de données. NULL pour les types de données non caractère.|  
  
3.  Si *nom* est n’importe quel objet de base de données autre qu’un type de données, **sp_help** retourne ce résultat des jeux de résultats de jeu et également supplémentaires, en fonction du type d’objet spécifié.  
  
    |Nom de colonne|Type de données|Description|  
    |-----------------|---------------|-----------------|  
    |**Nom**|**nvarchar(** 128 **)**|Nom de la table|  
    |**Propriétaire**|**nvarchar(** 128 **)**|Propriétaire de la table|  
    |**Type**|**nvarchar(** 31 **)**|Type de la table|  
    |**Created_datetime**|**datetime**|Date de création de la table|  
  
     En fonction de l’objet de base de données spécifié, **sp_help** retourne des jeux de résultats supplémentaires.  
  
     Si *nom* est une table système, une table ou une vue, **sp_help** retourne les jeux de résultats suivant. Toutefois, le jeu de résultats qui indique à quel endroit se trouve le fichier de données sur un groupe de fichiers n'est pas retourné pour une vue.  
  
    -   Jeu de résultats supplémentaire retourné sur des objets de colonne :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**Column_name**|**nvarchar(** 128 **)**|Nom de colonne.|  
        |**Type**|**nvarchar(** 128 **)**|Type de données de la colonne.|  
        |**Calculée**|**varchar(** 35 **)**|Indique si les valeurs de la colonne sont calculées : Oui ou Non.|  
        |**Longueur**|**Int**|Longueur de colonne en octets.<br /><br /> Remarque : Si le type de données de colonne est un type de valeur élevée (**varchar (max)**, **nvarchar (max)**, **varbinary (max)**, ou **xml**), la valeur sera afficher en tant que -1.|  
        |**PREC**|**char(** 5 **)**|Précision de la colonne|  
        |**Échelle**|**char(** 5 **)**|Échelle de la colonne|  
        |**Nullable**|**varchar(** 35 **)**|Indique si les valeurs NULL sont autorisées dans la colonne : Oui ou Non.|  
        |**TrimTrailingBlanks**|**varchar(** 35 **)**|Élimine les vides. Retourne Oui ou Non.|  
        |**FixedLenNullInSource**|**varchar(** 35 **)**|Pour compatibilité descendante uniquement.|  
        |**Classement**|**sysname**|Classement de la colonne. NULL pour les types de données non caractères.|  
  
    -   Jeu de résultats supplémentaire retourné sur des colonnes d'identité :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**Identity**|**nvarchar(** 128 **)**|Nom de la colonne dont le type de données déclaré est identité.|  
        |**Valeur initiale**|**numeric**|Valeur de départ de la colonne identité.|  
        |**Incrément**|**numeric**|Incrément à appliquer aux valeurs de la colonne.|  
        |**Pas pour la réplication**|**Int**|Propriété d’identité n’est pas appliquée lorsqu’une connexion de réplication, tel que **sqlrepl**, insère des données dans la table :<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   Jeu de résultats supplémentaire retourné sur des colonnes :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|Nom de la colonne d'identification unique.|  
  
    -   Jeu de résultats supplémentaire retourné sur des groupes de fichiers :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar(** 128 **)**|Groupe de fichiers dans lequel se trouvent les données : primaire, secondaire ou journal des transactions.|  
  
    -   Jeu de résultats supplémentaire retourné sur les index :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|Nom de l’index.|  
        |**Index_description**|**varchar(** 210 **)**|Description de l'index.|  
        |**index_keys**|**nvarchar(** 2078 **)**|Noms des colonnes servant de base à l'index. Retourne NULL pour les index columnstores optimisés en mémoire xVelocity.|  
  
    -   Jeu de résultats supplémentaire retourné sur des contraintes :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar(** 146 **)**|Type de contrainte.|  
        |**constraint_name**|**nvarchar(** 128 **)**|Nom de la contrainte.|  
        |**delete_action**|**nvarchar(** 9 **)**|Indique si l'action DELETE est : NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT, ou N/A.<br /><br /> Uniquement applicable aux contraintes FOREIGN KEY.|  
        |**update_action**|**nvarchar(** 9 **)**|Indique si l'action UPDATE est : NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT, ou N/A.<br /><br /> Uniquement applicable aux contraintes FOREIGN KEY.|  
        |**status_enabled**|**varchar(** 8 **)**|Indique si la contrainte est activée : Enabled, Disabled, ou N/A.<br /><br /> Uniquement applicable aux contraintes CHECK et FOREIGN KEY.|  
        |**status_for_replication**|**varchar(** 19 **)**|Indique si la contrainte concerne la réplication.<br /><br /> Uniquement applicable aux contraintes CHECK et FOREIGN KEY.|  
        |**constraint_keys**|**nvarchar(** 2078 **)**|Nom des colonnes qui constituent la contrainte ou, pour les valeurs par défaut ou les règles, le texte qui définit la valeur par défaut ou la règle.|  
  
    -   Jeu de résultats supplémentaire retourné sur des objets de référence :  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**Table est référencée par**|**nvarchar(** 516 **)**|Identifie les autres objets de base de données qui font référence à la table.|  
  
    -   Jeu de résultats supplémentaire retourné sur les procédures stockées, les fonctions ou les procédures stockées étendues.  
  
        |Nom de colonne|Type de données|Description|  
        |-----------------|---------------|-----------------|  
        |**Parameter_name**|**nvarchar(** 128 **)**|Nom du paramètre de la procédure stockée.|  
        |**Type**|**nvarchar(** 128 **)**|Type de données du paramètre de la procédure stockée.|  
        |**Longueur**|**smallint**|Longueur maximale de stockage physique, en octets.|  
        |**PREC**|**Int**|Précision ou nombre total de chiffres.|  
        |**Échelle**|**Int**|Nombre de chiffres situés à droite du séparateur décimal.|  
        |**Param_order**|**smallint**|Ordre du paramètre.|  
  
## <a name="remarks"></a>Notes  
 Le **sp_help** procédure recherche un objet dans la base de données actuelle uniquement.  
  
 Lorsque *nom* n’est pas spécifié, **sp_help** de l’objet listes de noms, les propriétaires et les types d’objets pour tous les objets dans la base de données actuelle. **sp_helptrigger** fournit des informations sur les déclencheurs.  
  
 **sp_help** expose uniquement les colonnes d’index pouvant être ordonnées ; par conséquent, elle n’expose pas d’informations sur les index XML ou spatiaux.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . L’utilisateur doit avoir au moins une autorisation *objname*. Pour consulter des clés de contrainte, des valeurs par défaut ou des règles de colonne, vous devez disposer de l'autorisation VIEW DEFINITION sur la table.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-information-about-all-objects"></a>A. Retour d'informations sur tous les objets  
 L'exemple suivant fournit des informations sur chaque objet de la base de données `master`.  
  
```  
USE master;  
GO  
EXEC sp_help;  
GO  
```  
  
### <a name="b-returning-information-about-a-single-object"></a>B. Retour d'informations sur un objet unique  
 L'exemple suivant affiche des informations sur la table `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help 'Person.Person';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpindex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [sp_helprotect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sysobjects &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  
