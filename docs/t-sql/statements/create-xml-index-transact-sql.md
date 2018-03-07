---
title: "CRÉER l’INDEX XML (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- XML_TSQL
- CREATE_XML_INDEX_TSQL
- XML INDEX
- CREATE_XML_TSQL
- XML
- CREATE XML
- CREATE XML INDEX
- XML_INDEX_TSQL
- FOR_XML_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE XML INDEX statement
- CREATE INDEX statement
- index creation [SQL Server], XML indexes
- XML indexes [SQL Server], creating
ms.assetid: c510cfbc-68be-4736-b3cc-dc5b7aa51f14
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 133c957937d1c05cd108eeb2deb0847cd7944771
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="create-xml-index-transact-sql"></a>CREATE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crée un index XML sur une table spécifiée. Un index peut être créé avant que la table soit remplie de données. Vous pouvez créer des index XML sur des tables dans une autre base de données en spécifiant un nom de base de données qualifié.  
  
> [!NOTE]  
>  Pour créer un index relationnel, consultez [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md). Pour plus d’informations sur la création d’un index spatial, consultez [CREATE SPATIAL INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-spatial-index-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Create XML Index   
CREATE [ PRIMARY ] XML INDEX index_name   
    ON <object> ( xml_column_name )  
    [ USING XML INDEX xml_index_name   
        [ FOR { VALUE | PATH | PROPERTY } ] ]  
    [ WITH ( <xml_index_option> [ ,...n ] ) ]  
[ ; ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_name  
}  
  
<xml_index_option> ::=  
{   
    PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
}  
  
```  
  
## <a name="arguments"></a>Arguments  
 [PRIMARY] XML  
 Crée un index XML sur le **xml** colonne. Lorsque PRIMARY est spécifié, un index cluster est créé avec la clé cluster créée à partir de la clé de clustering de la table utilisateur et d'un identificateur de nœud XML. Chaque table peut comporter jusqu'à 249 index XML. Tenez compte des points suivants lorsque vous créez un index XML :  
  
-   Un index cluster doit exister dans la clé primaire de la table utilisateur.  
  
-   La clé de clustering de la table utilisateur est limitée à 15 colonnes.  
  
-   Chaque **xml** colonne dans une table peut avoir un seul index XML primaire et plusieurs index XML secondaires.  
  
-   Un index XML primaire sur une **xml** colonne doit exister avant de pouvoir créer un index XML secondaire sur la colonne.  
  
-   Un index XML peut uniquement être créé sur un seul **xml** colonne. Vous ne pouvez pas créer un index XML sur un site non**xml** colonne, ni créer un index relationnel sur une **xml** colonne.  
  
-   Vous ne peut pas créer un index XML primaire ou secondaire, sur un **xml** colonne dans une vue, sur une variable de table incluse avec **xml** des colonnes, ou **xml** variables de type.  
  
-   Impossible de créer un index XML primaire sur une calculée **xml** colonne.  
  
-   Les valeurs de l'option SET doivent être identiques à celles requises pour les vues indexées et les index de colonne calculée. Plus précisément, l’option ARITHABORT doit être définie à ON lors de la création d’un index XML lorsque les valeurs d’insertion, la suppression ou la mise à jour dans le **xml** colonne.  
  
 Pour plus d’informations, consultez [Index XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
 *index_name*  
 Nom de l'index. Les noms d'index doivent être uniques dans une table, mais ne doivent pas être nécessairement uniques dans une base de données. Les noms d’index doivent respecter les règles de [identificateurs](../../relational-databases/databases/database-identifiers.md).  
  
 Les noms d’index XML primaires ne peut pas commencer par les caractères suivants :  **#** ,  **##** ,  **@** , ou  **@@** .  
  
 *xml_column_name*  
 Est la **xml** colonne sur laquelle l’index est basé. Seul **xml** colonne peut être spécifiée dans une définition d’index XML unique ; Toutefois, plusieurs index XML secondaires peuvent être créés sur un **xml** colonne.  
  
 À l’aide de l’INDEX XML *xml_index_name*  
 Spécifie l'index XML primaire à utiliser pour créer un index XML secondaire.  
  
 FOR { VALUE | PATH | PROPERTY }  
 Spécifie le type d'index XML secondaire.  
  
 VALUE  
 Crée un index XML secondaire sur les colonnes dans lesquelles les colonnes de clé (valeur et chemin de nœud) proviennent de l'index XML primaire.  
  
 PATH  
 Crée un index XML secondaire sur les colonnes créées sur des valeurs de chemin et des valeurs de nœud dans l'index XML primaire. Dans l'index secondaire PATH, les valeurs de chemin et de nœud sont des colonnes clés qui permettent de rechercher efficacement des chemins.  
  
 PROPERTY  
 Crée un index XML secondaire sur les colonnes (valeur PK, de chemin et de nœud) de l'index XML primaire où PK est la clé primaire de la table de base.  
  
 **\<object>::=**  
  
 Objet qualifié complet ou partiel à indexer.  
  
 *database_name*  
 Nom de la base de données.  
  
 *schema_name*  
 Nom du schéma auquel appartient la table.  
  
 *table_name*  
 Nom de la table à indexer.  
  
 **\<xml_index_option> ::=** 
  
 Spécifie les options à utiliser lorsque vous créez l'index.  
  
 PAD_INDEX  **=**  {ON | **OFF** }  
 Spécifie le remplissage de l'index. La valeur par défaut est OFF.  
  
 ON  
 Le pourcentage d’espace libre spécifié par *fillfactor* est appliqué aux pages de niveau intermédiaire de l’index.  
  
 DÉSACTIVER ou *fillfactor* n’est pas spécifié  
 Les pages de niveau intermédiaire sont presque entièrement remplies, ce qui laisse suffisamment d'espace libre pour au moins une ligne de la taille maximale permise par l'index, en prenant en compte l'ensemble de clés sur les pages intermédiaires.  
  
 L'option PAD_INDEX est utile seulement si FILLFACTOR est spécifié, car PAD_INDEX utilise le pourcentage spécifié par FILLFACTOR. Si le pourcentage défini pour FILLFACTOR n'est pas suffisamment élevé pour autoriser une ligne, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] remplace en interne le pourcentage de façon à ce qu'il autorise le minimum. Le nombre de lignes sur une page d’index intermédiaire n’est jamais inférieur à 2, quelle que soit la valeur de faible *fillfactor*.  
  
 FILLFACTOR **=***fillfactor*  
 Spécifie un pourcentage indiquant le taux de remplissage appliqué par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au niveau feuille de chaque page d'index lors de la création ou de la reconstruction de l'index. *facteur de remplissage* doit être un entier compris entre 1 et 100. La valeur par défaut est 0. Si *fillfactor* est 100 ou 0, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] crée des index avec des pages de niveau feuille intégralement remplies.  
  
> [!NOTE]  
>  Les taux de remplissage 0 et 100 sont identiques en tous points.  
  
 La valeur FILLFACTOR s'applique uniquement lors de la création ou de la reconstruction de l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne conserve pas dynamiquement dans les pages le pourcentage d'espace libre défini. Pour afficher le paramètre du facteur de remplissage, utilisez la [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vue de catalogue.  
  
> [!IMPORTANT]  
>  La création d'un index cluster avec un facteur de remplissage FILLFACTOR inférieur à 100 affecte la quantité d'espace de stockage qu'occupent les données, car le [!INCLUDE[ssDE](../../includes/ssde-md.md)] redistribue les données lorsqu'il crée l'index cluster.  
  
 Pour plus d’informations, consultez [Spécifier un facteur de remplissage pour un index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 SORT_IN_TEMPDB  **=**  {ON | **OFF** }  
 Spécifie s’il faut stocker les résultats temporaires du tri dans **tempdb**. La valeur par défaut est OFF.  
  
 ON  
 Les résultats de tri intermédiaires qui sont utilisés pour créer l’index sont stockés dans **tempdb**. Cela peut réduire le temps nécessaire pour créer un index si **tempdb** est un ensemble de disques que la base de données utilisateur. Toutefois, une plus grande quantité d'espace disque est alors utilisée lors de la création de l'index.  
  
 OFF  
 Les résultats de tri intermédiaires sont stockés dans la même base de données que l'index.  
  
 Outre l’espace nécessaire dans la base de données utilisateur pour créer l’index, **tempdb** doit avoir environ la même quantité d’espace supplémentaire pour stocker les résultats de tri intermédiaires. Pour plus d’informations, consultez [Option SORT_IN_TEMPDB pour les index](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md).  
  
 IGNORE_DUP_KEY **= OFF**  
 N'a aucun effet pour les index XML, car le type d'index n'est jamais unique. N'activez pas cette option (ON), sinon une erreur est déclenchée.  
  
 DROP_EXISTING  **=**  {ON | **OFF** }  
 Spécifie que l'index XML nommé préexistant est supprimé et reconstruit. La valeur par défaut est OFF.  
  
 ON  
 L'index existant est supprimé et recréé. Le nom d'index défini doit être identique à celui de l'index existant. Toutefois, la définition de l'index peut être modifiée. Par exemple, vous pouvez définir des colonnes, un ordre de tri, un schéma de partition ou des options d'indexation différentes.  
  
 OFF  
 Une erreur s'affiche si le nom d'index spécifié existe déjà.  
  
 Le type d'index ne peut pas être modifié à l'aide de DROP_EXISTING. En outre, un index primaire XML ne peut pas être redéfini comme index XML secondaire, et inversement.  
  
 EN LIGNE **= OFF**  
 Indique que les tables sous-jacentes et les index associés ne sont pas disponibles pour les requêtes et la modification de données pendant l'opération d'index. Dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les constructions d'index en ligne ne sont pas prises en charge pour les index XML. Si cette option est activée (ON) pour un index XML, une erreur est déclenchée. Omettez l'option ONLINE ou attribuez la valeur OFF à ONLINE.  
  
 Une opération d'index hors connexion qui crée, reconstruit ou supprime un index XML acquiert un verrou Sch-M (Modification du schéma) sur la table. Cela empêche tous les utilisateurs d'accéder à la table sous-jacente pendant la durée de l'opération.  
  
> [!NOTE]  
>  Les opérations d'index en ligne ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 Indique si les verrous de ligne sont autorisés ou non. La valeur par défaut est ON.  
  
 ON  
 Les verrous de ligne sont autorisés lors de l'accès à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de ligne sont utilisés.  
  
 OFF  
 Les verrous de ligne ne sont pas utilisés.  
  
 ALLOW_PAGE_LOCKS **=** { **ON** | OFF }  
 Indique si les verrous de page sont autorisés. La valeur par défaut est ON.  
  
 ON  
 Les verrous de page sont autorisés lors de l'accès à l'index. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] détermine le moment où les verrous de page sont utilisés.  
  
 OFF  
 Les verrous de page ne sont pas utilisés.  
  
 MAXDOP **=***max_degree_of_parallelism*  
 Remplace le [configurer le degré maximal de parallélisme Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) option de configuration pour la durée de l’opération d’index. Utilisez MAXDOP pour limiter le nombre de processeurs utilisés dans une exécution de plan parallèle. Le nombre maximal de processeurs est égal à 64.  
  
> [!IMPORTANT]  
>  Bien que l'option MAXDOP soit prise en charge syntaxiquement pour tous les index XML, pour un index XML primaire, CREATE XML INDEX utilise uniquement un processeur unique.  
  
 *max_degree_of_parallelism* peut être :  
  
 1  
 Supprime la création de plans parallèles.  
  
 \>1  
 Limite le nombre maximal de processeurs utilisés dans l'indexation parallèle au nombre défini ou à un nombre inférieur en fonction de la charge de travail actuelle du système.  
  
 0 (valeur par défaut)  
 Utilise le nombre réel de processeurs ou un nombre de processeurs inférieur en fonction de la charge de travail actuelle du système.  
  
 Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Opérations d’index parallèles ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="remarks"></a>Notes  
 Les colonnes calculées dérivées **xml** types de données peuvent être indexées comme colonne clée ou incluse non-clés tant que le type de données de colonne calculée est autorisé en tant qu’une colonne clé d’index ou une colonne non-clé. Impossible de créer un index XML primaire sur une calculée **xml** colonne.  
  
 Pour afficher des informations sur les index XML, utilisez la [sys.xml_indexes](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md) affichage catalogue.  
  
 Pour plus d’informations sur les index XML, consultez [index XML &#40; SQL Server &#41; ](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
## <a name="additional-remarks-on-index-creation"></a>Remarques supplémentaires sur la création d'index  
 Pour plus d’informations sur la création d’index, consultez la section « Remarques » dans [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-primary-xml-index"></a>A. Création d'un index XML primaire  
 L'exemple suivant crée un index XML primaire sur la colonne `CatalogDescription` de la table `Production.ProductModel`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT * FROM sys.indexes  
            WHERE name = N'PXML_ProductModel_CatalogDescription')  
    DROP INDEX PXML_ProductModel_CatalogDescription   
        ON Production.ProductModel;  
GO  
CREATE PRIMARY XML INDEX PXML_ProductModel_CatalogDescription  
    ON Production.ProductModel (CatalogDescription);  
GO  
```  
  
### <a name="b-creating-a-secondary-xml-index"></a>B. Création d’un index XML secondaire  
 L'exemple suivant crée un index XML secondaire sur la colonne `CatalogDescription` de la table `Production.ProductModel`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.indexes  
            WHERE name = N'IXML_ProductModel_CatalogDescription_Path')  
    DROP INDEX IXML_ProductModel_CatalogDescription_Path  
        ON Production.ProductModel;  
GO  
CREATE XML INDEX IXML_ProductModel_CatalogDescription_Path   
    ON Production.ProductModel (CatalogDescription)  
    USING XML INDEX PXML_ProductModel_CatalogDescription FOR PATH ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [Index XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Index XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  

