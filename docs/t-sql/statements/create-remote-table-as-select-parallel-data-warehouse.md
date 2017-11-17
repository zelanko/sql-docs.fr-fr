---
title: CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse) | Documents Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: 
ms.prod_service: pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16ef8191-7587-45a3-9ee9-7d99b7088de3
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0318d108d6dfaaa374af9a1ab8a148ff960dfcd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-remote-table-as-select-parallel-data-warehouse"></a>CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Sélectionne les données d’une [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] de base de données et copie des données vers une nouvelle table dans un SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données sur un serveur distant. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]utilise l’application, avec tous les avantages MPP du traitement des requêtes, pour sélectionner les données pour la copie distante. Utiliser pour les scénarios qui requièrent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnalité.  
  
 Pour configurer le serveur distant, consultez « Copie de la Table distante » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE REMOTE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name     AT ('<connection_string>')  
    [ WITH ( BATCH_SIZE = batch_size ) ]  
    AS <select_statement>  
[;]  
  
<connection_string> ::=   
    Data Source = { IP_address | hostname } [, port ]; User ID = user_name ;Password = password;  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Créer la table distante dans la base de données. *database_name* est un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. Valeur par défaut est la base de données par défaut pour la connexion de l’utilisateur sur la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 *schema_name*  
 Le schéma de la nouvelle table. Valeur par défaut est le schéma par défaut pour la connexion de l’utilisateur sur la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 *table_name*  
 Le nom de la nouvelle table. Pour plus d’informations sur autorisées des noms de table, consultez « Règles d’affectation de noms d’objet » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 La table distante est créée en tant que segment. Il n’a pas de contraintes de validation ou de déclencheurs. Le classement des colonnes de la table distante est le même que le classement des colonnes de table source. Cela s’applique aux colonnes de type **char**, **nchar**, **varchar**, et **nvarchar**.  
  
 *chaîne_connexion*  
 Une chaîne de caractères qui spécifie le `Data Source`, `User ID`, et `Password` paramètres pour la connexion au serveur distant et à la base de données.  
  
 La chaîne de connexion est une liste délimitée par des points-virgules de paires clé / valeur. Mots clés ne respectent pas la casse. Les espaces entre les paires clé / valeur sont ignorés. Toutefois, les valeurs peuvent être sensible à la casse, en fonction de la source de données.  
  
 *Source de données*  
 Le paramètre qui spécifie le nom ou adresse IP et TCP numéro de port pour le SMP distant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *nom d’hôte* ou *adresse_IP*  
 Nom de l’ordinateur de serveur distant ou l’adresse IPv4 du serveur distant. Les adresses IPv6 ne sont pas pris en charge. Vous pouvez spécifier un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance nommée dans le format **ordinateur\instance** ou **IP_address\Instance_Name**. Le serveur doit être distant et par conséquent ne peut pas être spécifié en tant que (local).  
  
 TCP *port* nombre  
 Le numéro de port TCP pour la connexion. Vous pouvez spécifier un numéro de port TCP comprise entre 0 et 65 535 pour une instance de SQL Server qui n’est pas à l’écoute sur le port par défaut 1433. Par exemple : **ServerA, 1450** ou **10.192.14.27,1435**  
  
> [!NOTE]  
>  Il est recommandé de se connecter à un serveur distant à l’aide de l’adresse IP. Selon votre configuration réseau, la connexion à l’aide du nom de l’ordinateur peut nécessiter des étapes supplémentaires pour votre serveur DNS de l’appliance non permet de résoudre le nom au serveur approprié. Cette étape n’est pas nécessaire lors de la connexion avec une adresse IP. Pour plus d’informations, consultez « Utiliser un redirecteur DNS pour les noms DNS de l’Appliance Non résolution (système de plateforme Analytique) » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 *nom_utilisateur*  
 Valide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom de connexion d’authentification. Nombre maximal de caractères est 128.  
  
 *mot de passe*  
 Mot de passe de connexion. Nombre maximal de caractères est 128.  
  
 *batch_size*  
 Le nombre maximal de lignes par lot. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]envoie les lignes par lots sur le serveur de destination. *Batch_size* est un nombre entier > = 0. Valeur par défaut est 0.  
  
 AVEC *common_table_expression*  
 Spécifie un jeu de résultats nommé temporaire, désigné par le terme d'expression de table commune (CTE, Common Table Expression). Pour plus d’informations, consultez [avec common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 Sélectionnez \<select_criteria > le prédicat de requête qui spécifie les données remplira la table distante. Pour plus d’informations sur l’instruction SELECT, consultez [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite :  
  
-   L’autorisation SELECT sur chaque objet dans la clause SELECT.  
  
-   Requiert l’autorisation CREATE TABLE dans la base de données de destination SMP.  
  
-   Requiert ALTER, INSERT et des autorisations SELECT sur le schéma SMP de destination.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 En cas de copie des données dans la base de données distante, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sera abandonner l’opération, enregistre une erreur et essayez de supprimer la table distante. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ne garantit pas un nettoyage réussi de la nouvelle table.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 **Serveur de Destination distant**:  
  
-   TCP est la valeur par défaut et uniquement pris en charge de protocole pour se connecter à un serveur distant.  
  
-   Le serveur de destination doit être un serveur autre que l’appliance. CREATE REMOTE TABLE ne peut pas être utilisé pour copier des données à partir d’un équipement à un autre.  
  
-   L’instruction CREATE REMOTE TABLE seulement crée de nouvelles tables. Par conséquent, la nouvelle table ne peut pas exister. La base de données distante et le schéma doivent déjà exister.  
  
-   Le serveur distant doit disposer d’espace stocker les données qui sont transférées à partir de l’appareil à le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données distante.  
  
 **Instruction SELECT**:  
  
-   Les clauses ORDER BY et TOP ne sont pas pris en charge dans les critères de sélection.  
  
-   CRÉER une TABLE distante ne peut pas être exécutée à l’intérieur d’une transaction active, ou lorsque le paramètre de validation automatique désactivé n’est actif pour la session.  
  
 [SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) n’a aucun effet sur cette instruction. Pour obtenir un comportement similaire, utilisez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
 Après avoir créé la table distante, la table de destination n’est pas verrouillée jusqu'à ce que la copie commence. Par conséquent, il est possible qu’un autre processus supprimer la table distante après sa création et avant le démarrage de la copie. Lorsque cela se produit, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] génère une erreur et la copie échouera.  
  
## <a name="metadata"></a>Métadonnées  
 Utilisez [sys.dm_pdw_dms_workers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md) pour afficher la progression de la copie les données sélectionnées au serveur distant SMP. Lignes avec le type PARALLEL_COPY_READER contiennent ces informations.  
  
## <a name="security"></a>Sécurité  
 CRÉER une TABLE distante utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification pour se connecter à l’instance distante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance ; elle n’utilise pas l’authentification Windows.  
  
 Le [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] réseau externe doit être protégée par un pare-feu, à l’exception des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ports, les ports d’administration et les ports de gestion.  
  
 Pour aider à empêcher la perte accidentelle de données ou l’altération, le compte d’utilisateur qui est utilisé pour copier à partir de l’application à la base de données de destination doit avoir uniquement les autorisations minimales requises sur la base de données de destination.  
  
 Paramètres de connexion permettent de vous connecter à la SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance SSL protège les données de nom et mot de passe utilisateur, mais avec des données réelles qui est envoyées en texte clair. Lorsque cela se produit, un utilisateur malveillant pourrait intercepter le texte de l’instruction CREATE REMOTE TABLE, qui contient le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom d’utilisateur et mot de passe pour se connecter à la SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance. Pour éviter ce risque, utilisez le chiffrement des données sur la connexion à la SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
##  <a name="Examples"></a> Exemples  
  
### <a name="a-creating-a-remote-table"></a>A. Création d’une table distante  
 Cet exemple crée un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table distante en SMP appelé `MyOrdersTable` sur la base de données `OrderReporting` et schéma `Orders`. Le `OrderReporting` base de données est sur un serveur nommé `SQLA` qui écoute sur le port par défaut 1433. La connexion au serveur utilise les informations d’identification de l’utilisateur `David`, dont un mot de passe est `e4n8@3`.  
  
```  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
AS SELECT <select_criteria>;  
```  
  
### <a name="b-querying-the-sysdmpdwdmsworkers-dmv-for-remote-table-copy-status"></a>B. Interrogation de la vue de gestion dynamique sys.dm_pdw_dms_workers pour l’état de copie de table distante  
 Cette requête montre comment afficher l’état de la copie d’une copie de la table distante.  
  
```  
SELECT * FROM sys.dm_pdw_dms_workers   
WHERE type = 'PARALLEL_COPY_READER';  
```  
  
### <a name="c-using-a-query-join-hint-with-create-remote-table"></a>C. À l’aide d’un indicateur de requête de jointure avec CREATE REMOTE TABLE  
 Cette requête affiche la syntaxe de base pour l’utilisation d’un indicateur de requête de jointure avec CREATE REMOTE TABLE. Une fois la requête est envoyée au nœud de contrôle, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en cours d’exécution sur les nœuds de calcul, s’applique la stratégie de jointure de hachage lors de la génération du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plan de requête. Pour plus d’informations sur les indicateurs de jointure et l’utilisation de la clause OPTION, consultez [Clause OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
USE ssawPDW;  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
    AS SELECT T1.* FROM OrderReporting.Orders.MyOrdersTable T1   
    JOIN OrderReporting.Order.Customer T2  
    ON T1.CustomerID=T2.CustomerID OPTION (HASH JOIN);  
```  
  
  


