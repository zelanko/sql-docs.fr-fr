---
title: Options (Page script de l’Explorateur d’objet SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81e4bafbd596894a8cecbeb707a5d8be698c1f3b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764401"
---
# <a name="options-sql-server-object-explorer-scripting-page"></a>Options (Page script de l’Explorateur d’objet SQL Server)
  Utilisez cette page pour définir les options de script qui s’appliquent aux commandes suivantes dans les menus contextuels d’objet de **l’Explorateur d’objets**:  
  
-   Commandes **Edition** pour les vues et tables utilisateur.  
  
-   **Script \<objet > en tant que** commandes pour les objets créés par l’utilisateur.  
  
-   Commandes **Modifier** pour les objets créés par l’utilisateur.  
  
-   Cette page définit également les valeurs par défaut des options de script de **l’Assistant Génération de scripts SQL Server**.  
  
## <a name="remarks"></a>Notes  
 Le **modifier** et **modifier** commandes peuvent produire des résultats différents de la **Script \<objet > en tant que** commande pour le même paramètre d’option. Les commandes **Edition** et **Modifier** sont conçues pour modifier des objets de la base de données active durant une session de l’Éditeur de requête. Le **Script \<objet > en tant que** commande est conçue pour générer un script afin qu’il peut être utilisé ultérieurement pour créer des objets.  
  
## <a name="options"></a>Options  
 Spécifiez les options de script en les sélectionnant parmi les paramètres disponibles dans la liste située à droite de chaque option.  
  
### <a name="general-scripting-options"></a>Options de script générales  
 **Délimiter des instructions individuelles**  
 Sépare les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] par un délimiteur de traitement. Pour modifier le délimiteur de traitement par défaut de **l’Éditeur de requête**, sélectionnez **Outils**/**Options**/**Exécution de la requête**/**SQL Server**/**Général**/**Délimiteur de traitement**. La valeur par défaut est FALSE. Pour plus d’informations, consultez [accédez &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/sql-server-utilities-statements-go).  
  
 **Inclure des en-têtes descriptifs**  
 Ajoute des commentaires descriptifs au script en séparant le script en sections pour chaque objet. La valeur par défaut est True. Pour plus d’informations, consultez [commentaire &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comment-transact-sql).  
  
 **Inclure des options VarDecimal**  
 Inclut les options de stockage VarDecimal. La valeur par défaut est FALSE. Pour plus d’informations, consultez et [sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).  
  
 **Générer le script de suivi des modifications**  
 Inclut des informations de suivi des modifications dans le script.  
  
 **Générer un script pour la version du serveur**  
 Crée un script qui peut être exécuté sur la version sélectionnée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les fonctionnalités qui sont des nouveautés de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ne peuvent pas faire l'objet d'un script pour les versions antérieures. Certains scripts qui sont créés pour [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ne peuvent pas être exécutés sur les serveurs exécutant une version antérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ou sur une base de données qui possède un [paramètre de niveau de compatibilité de base de données](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)antérieur.  
  
 **Générer un script pour les catalogues de texte intégral**  
 Inclut un script pour les catalogues de texte intégral. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql).  
  
 **UTILISATION de script \<base de données >**  
 Ajoute l’instruction USE DATABASE au script pour créer des objets de base de données dans le contexte de la base de données de **l’Explorateur d’objets** active. Lorsqu'il est prévu que le script sera utilisé dans une base de données différente, sélectionnez False afin d'omettre l'instruction. La valeur par défaut est True. Pour plus d’informations, consultez [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
### <a name="object-scripting-options"></a>Options de scripts d'objets  
 **Générer un script pour les objets dépendants**  
 Génère un script pour les objets supplémentaires qui sont requis lorsque le script de l'objet sélectionné est exécuté. La valeur par défaut est FALSE.  
  
 **Inclure la clause If NOT EXISTS**  
 Inclut une instruction permettant de vérifier qu'un objet n'existe pas dans la base de données avant de créer l'objet. La valeur par défaut est FALSE. Pour plus d’informations, consultez [IF... AUTRE &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/if-else-transact-sql) et [EXISTS &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/exists-transact-sql).  
  
 **Noms d'objet de qualification de schéma**  
 Qualifie les noms d'objets avec le schéma de l'objet. La valeur par défaut est FALSE. Pour plus d’informations, consultez [Créer un schéma de base de données](../../relational-databases/security/authentication-access/create-a-database-schema.md).  
  
 **Générer un script pour les propriétés étendues**  
 Inclut les propriétés étendues dans le script, si l'objet en possède. La valeur par défaut est FALSE. Pour plus d’informations, consultez [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).  
  
 **Propriétaire de script**  
 Inclut le propriétaire dans le script généré. La valeur par défaut est FALSE.  
  
 **Générer un script pour les autorisations**  
 Inclut les autorisations sur les objets de base de données dans le script. La valeur par défaut est True. Pour plus d’informations, consultez [autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
### <a name="tableview-options"></a>Options de table/vue  
 Les options suivantes s'appliquent uniquement aux scripts des tables et des vues.  
  
 **Convertir les types de données définis par l'utilisateur en types de base**  
 Convertit les types de données définis par l'utilisateur en types de base à partir desquels ils ont été créés. Utilisez True lorsque les types de données définis par l'utilisateur de la base de données source n'existent pas dans la base de données où le script sera exécuté. Utilisez False pour conserver les types de données définis par l'utilisateur. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).  
  
 **Générer des commandes SET ANSI PADDING**  
 Ajoute l'instruction SET ANSI_PADDING avant et après chaque instruction CREATE TABLE. La valeur par défaut est True. Pour plus d’informations, consultez [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Inclure un classement**  
 Inclut un classement dans la définition de colonne. La valeur par défaut est True. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 **Inclure la propriété IDENTITY**  
 Inclut des définitions pour la valeur de départ IDENTITY et l'incrément IDENTITY. La valeur par défaut est True. Pour plus d’informations, consultez [IDENTITY &#40;propriété&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).  
  
 **Références aux clés étrangères de qualification de schéma**  
 Ajoute le nom de schéma aux références de table des contraintes FOREIGN KEY. La valeur par défaut est True.  
  
 **Valeurs par défaut et règles liées aux scripts**  
 Inclut les appels aux procédures stockées liées **sp_bindefault** et **sp_bindrule** . La valeur par défaut est True. Pour plus d’informations, consultez [sp_bindefault &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-bindefault-transact-sql) et [sp_bindrule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindrule-transact-sql).  
  
 **Générer un script pour les contraintes CHECK**  
 Ajoute des [contraintes CHECK](../../relational-databases/tables/unique-constraints-and-check-constraints.md) au script. La valeur par défaut est True.  
  
 **Valeurs de script par défaut**  
 Inclut les valeurs de colonne par défaut dans le script. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
 **Générer un script pour les groupes de fichiers**  
 Spécifie le groupe de fichiers dans la clause ON pour des définitions de table. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
 **Générer un script pour les clés étrangères**  
 Inclut des [contraintes FOREIGN KEY](../../relational-databases/tables/primary-and-foreign-key-constraints.md) dans le script. La valeur par défaut est FALSE.  
  
 **Générer un script pour les index de recherche en texte intégral**  
 Inclut les index de recherche en texte intégral dans le script. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).  
  
 **Générer un script pour les index**  
 Inclut des index cluster, non cluster et XML dans le script. La valeur par défaut est True. Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
 **Générer un script pour les schémas de partition**  
 Inclut des schémas de partition de table dans le script. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql).  
  
 **Générer un script pour les clés primaires**  
 Inclut des [contraintes de clé primaire et de clé étrangère](../../relational-databases/tables/primary-and-foreign-key-constraints.md) dans le script. La valeur par défaut est True.  
  
 **Générer un script pour les statistiques**  
 Inclut des statistiques définies par l'utilisateur dans le script. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Générer un script pour les déclencheurs**  
 Inclut des déclencheurs dans le script. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Générer un script pour les clés uniques**  
 Inclut des [contraintes uniques et des contraintes de validation](../../relational-databases/tables/unique-constraints-and-check-constraints.md) dans le script. La valeur par défaut est FALSE.  
  
 **Générer un script pour les colonnes de vue**  
 Déclare des colonnes de vue dans les en-têtes de vue. La valeur par défaut est FALSE. Pour plus d’informations, consultez [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).  
  
 **ScriptDriIncludeSystemNames**  
 Inclut les noms de contraintes générés par le système pour appliquer l'intégrité référentielle déclarative. La valeur par défaut est FALSE. Pour plus d’informations, consultez [REFERENTIAL_CONSTRAINTS &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/referential-constraints-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Générer des scripts &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)  
  
  
