---
title: "Sp&#233;cifier des mappages de types de donn&#233;es pour un Serveur de publication Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publication Oracle [réplication SQL Server], mappage de type de données"
  - "types de données [réplication SQL Server], publication Oracle"
  - "mappage de types de données [réplication SQL Server]"
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Sp&#233;cifier des mappages de types de donn&#233;es pour un Serveur de publication Oracle
  Cette rubrique explique comment spécifier des mappages de type de données pour un Serveur de publication Oracle dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Bien qu'un jeu de mappages de type de données par défaut soit fourni pour les serveurs de publication Oracle, il peut être nécessaire de spécifier des mappages différents pour une publication donnée.  
  
 **Dans cette rubrique**  
  
-   **Pour spécifier des mappages de type de données pour un Serveur de publication Oracle, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifier les mappages de types de données sur le **le mappage de données** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue. Cette option est disponible à partir de la **Articles** page de l’Assistant Nouvelle Publication et **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [créer une Publication à partir d’une base de données Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md) et [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier un mappage de types de données  
  
1.  Sur le **Articles** page de l’Assistant Nouvelle Publication ou le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table, puis cliquez sur **Propriétés de l’Article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
3.  Sur le **le mappage de données** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue, sélectionnez des mappages dans le **Type de données d’abonné** colonne :  
  
    -   Pour certains types de données, il existe uniquement une seule possibilité de mappage dans laquelle la colonne de la grille de propriétés est en lecture seule.  
  
    -   Pour certains types, vous pouvez sélectionner plus d'un type. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande d'utiliser le mappage par défaut si l'application ne nécessite pas un mappage différent. Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez spécifier des mappages de type de données personnalisés par programme à l'aide des procédures stockées de réplication. Vous pouvez également définir les mappages par défaut qui sont utilisés lorsque les types de données de mappage entre [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de base de données de gestion (SGBD). Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### Pour définir des mappages de type de données personnalisés lors de la création d'un article appartenant à une publication Oracle  
  
1.  S'il n'en existe pas encore, créez une publication Oracle.  
  
2.  Sur le serveur de distribution, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Spécifiez la valeur **0** pour **@use_default_datatypes**. Pour plus d'informations, voir [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Sur le serveur de distribution, exécutez [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) pour afficher le mappage existant pour une colonne dans un article publié.  
  
4.  Sur le serveur de distribution, exécutez [sp_changearticlecolumndatatype](../../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, ainsi que **@publication**, **@article**et **@column** pour définir la colonne publiée. Spécifiez le nom du type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers lequel effectuer le mappage pour **@type**, ainsi que **@length**, **@precision**et **@scale**, le cas échéant.  
  
5.  Sur le serveur de distribution, exécutez [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Cela crée la vue utilisée pour générer l'instantané à partir de la publication Oracle.  
  
#### Pour spécifier un mappage comme mappage par défaut pour un type de données  
  
1.  (Facultatif) Sur le serveur de distribution sur une base de données, exécutez [sp_getdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md). Spécifier **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_version**, et d’autres paramètres nécessaires pour identifier le SGBD source. Les informations sur le type de données actuellement mappé dans le SGBD de destination sont retournées à l'aide des paramètres de sortie.  
  
2.  (Facultatif) Sur le serveur de distribution sur une base de données, exécutez [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md). Spécifier **@source_dbms** et d’autres paramètres requis pour filtrer le jeu de résultats. Notez la valeur de **mapping_id** pour le mappage souhaité dans le résultat défini.  
  
3.  Sur le serveur de distribution sur une base de données, exécutez [sp_setdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md).  
  
    -   Si vous connaissez la valeur souhaitée de **mapping_id** obtenu à l’étape 2, spécifiez-la pour **@mapping_id**.  
  
    -   Si vous ne connaissez pas le **mapping_id**, spécifiez les paramètres **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_type**, et tous les autres paramètres requis pour identifier un mappage existant.  
  
#### Pour rechercher les types de données valides pour un type de données Oracle donné  
  
1.  Sur le serveur de distribution sur une base de données, exécutez [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md). Spécifiez la valeur **ORACLE** pour **@source_dbms** et d’autres paramètres requis pour filtrer le jeu de résultats.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple modifie une colonne avec un type de données Oracle de nombre afin qu’elle est mappée à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type de données **numériques**(38,38), au lieu du type de données par défaut **float**.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_1.sql)]  
  
 Cet exemple de requête retourne les mappages par défaut et de remplacement pour le type de données Oracle 9 **CHAR**.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_2.sql)]  
  
 Cet exemple de requête retourne les mappages par défaut pour le type de données Oracle 9 **NUMBER** lorsqu'il est spécifié sans échelle ni précision.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_3.sql)]  
  
## Voir aussi  
 [Mappage de type de données pour les serveurs de publication Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Réplication hétérogène d'une base de données](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)  
  
  