---
title: Spécifier des mappages de types de données pour un Serveur de publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 27bf94ce5204e17fa694d8a9f9044aed59f13299
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116419"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a>Spécifier des mappages de types de données pour un Serveur de publication Oracle
  Cette rubrique explique comment spécifier des mappages de type de données pour un Serveur de publication Oracle dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Bien qu'un jeu de mappages de type de données par défaut soit fourni pour les serveurs de publication Oracle, il peut être nécessaire de spécifier des mappages différents pour une publication donnée.  
  
 **Dans cette rubrique**  
  
-   **Pour spécifier des mappages de type de données pour un Serveur de publication Oracle, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifiez des mappages de type de données sous l’onglet **Mappage de données** de la boîte de dialogue **Propriétés de l’article - \<Article>**. Celle-ci est disponible dans la page **Articles** de l’Assistant Nouvelle publication et la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d’informations sur l’utilisation de l’Assistant et sur l’accès à la boîte de dialogue, consultez [Créer une publication à partir d’une base de données Oracle](create-a-publication-from-an-oracle-database.md) et [Afficher et modifier les propriétés d’une publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-a-data-type-mapping"></a>Pour spécifier un mappage de types de données  
  
1.  Dans la page **Articles** de l’Assistant Nouvelle publication ou la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez une table et cliquez sur **Propriétés de l’article**.  
  
2.  Cliquez sur **Définir les propriétés de l'article de Table en surbrillance**.  
  
3.  Sous l’onglet **Mappage de données** de la boîte de dialogue **Propriétés de l’article - \<Article>**, sélectionnez des mappages dans la colonne **Type de données de l’Abonné** :  
  
    -   Pour certains types de données, il existe uniquement une seule possibilité de mappage dans laquelle la colonne de la grille de propriétés est en lecture seule.  
  
    -   Pour certains types, vous pouvez sélectionner plus d'un type. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande d'utiliser le mappage par défaut si l'application ne nécessite pas un mappage différent. Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez spécifier des mappages de type de données personnalisés par programme à l'aide des procédures stockées de réplication. Vous pouvez également définir les mappages par défaut qui sont utilisés lors du mappage de types de données entre [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et un système de gestion de base de données (SGBD) non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a>Pour définir des mappages de type de données personnalisés lors de la création d'un article appartenant à une publication Oracle  
  
1.  S'il n'en existe pas encore, créez une publication Oracle.  
  
2.  Sur le serveur de distribution, exécutez [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql). Spécifiez la valeur **0** pour **@use_default_datatypes**. Pour plus d'informations, voir [Define an Article](define-an-article.md).  
  
3.  Sur le serveur de distribution, exécutez [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) pour afficher le mappage existant pour une colonne dans un article publié.  
  
4.  Sur le serveur de distribution, exécutez [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql). Spécifiez le nom du serveur de publication Oracle pour **@publisher**, ainsi que **@publication**, **@article**et **@column** pour définir la colonne publiée. Spécifiez le nom du type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers lequel effectuer le mappage pour **@type**, ainsi que **@length**, **@precision**et **@scale**, le cas échéant.  
  
5.  Sur le serveur de distribution, exécutez [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Cela crée la vue utilisée pour générer l'instantané à partir de la publication Oracle.  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a>Pour spécifier un mappage comme mappage par défaut pour un type de données  
  
1.  (Facultatif) Exécutez [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)sur une base de données quelconque du serveur de distribution. Spécifiez **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_version**et tous les autres paramètres éventuellement requis pour identifier le SGBD source. Les informations sur le type de données actuellement mappé dans le SGBD de destination sont retournées à l'aide des paramètres de sortie.  
  
2.  (Facultatif) Exécutez [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)sur une base de données quelconque du serveur de distribution. Spécifiez **@source_dbms** et tous les autres paramètres éventuellement requis pour filtrer le jeu de résultats. Notez la valeur de **mapping_id** pour le mappage souhaité dans le jeu de résultats.  
  
3.  Exécutez [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)sur une base de données quelconque du serveur de distribution.  
  
    -   Si vous connaissez la valeur souhaitée de **mapping_id** obtenue à l'étape 2, spécifiez-la pour **@mapping_id**.  
  
    -   Si vous ne connaissez pas **mapping_id**, spécifiez les paramètres **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_type**et tous les autres paramètres éventuellement requis pour identifier un mappage existant.  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a>Pour rechercher les types de données valides pour un type de données Oracle donné  
  
1.  Exécutez [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)sur une base de données quelconque du serveur de distribution. Spécifiez la valeur **ORACLE** pour **@source_dbms** et tous les autres paramètres éventuellement requis pour filtrer le jeu de résultats.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Cet exemple modifie une colonne avec le type de données Oracle NUMBER afin qu'elle soit mappée vers le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `numeric`(38,38), à la place du type de données par défaut `float`.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 Cet exemple de requête retourne les mappages par défaut et de remplacement pour le type de données Oracle 9 `CHAR`.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 Cet exemple de requête retourne les mappages par défaut pour le type de données Oracle 9 `NUMBER` lorsqu'il est spécifié sans échelle ni précision.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a>Voir aussi  
 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Réplication hétérogène d’une base de données](../non-sql/heterogeneous-database-replication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Configurer un serveur de publication Oracle](../non-sql/configure-an-oracle-publisher.md)  
  
  
