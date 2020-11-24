---
description: Synonymes (Moteur de base de données)
title: Synonymes (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synonyms [SQL Server], about synonyms
ms.assetid: 6210e1d5-075f-47e4-ac8d-f84bcf26fbc0
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 74f5c5dcf2f2e1891daca22d70ebb9d9f1d9119f
ms.sourcegitcommit: a49a66dbda0cb16049e092b49c8318ac3865af3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94983113"
---
# <a name="synonyms-database-engine"></a>Synonymes (Moteur de base de données)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un synonyme est un objet de base de données utilisé aux fins suivantes :  
  
-   Il fournit un nom de remplacement pour un autre objet de base de données, appelé « objet de base », qui peut exister sur un serveur local ou distant.  
  
-   Il fournit une couche d'abstraction qui protège une application cliente contre les modifications apportées au nom ou à l'emplacement de l'objet de base.  
  
Par exemple, supposons que la table **Employee** de [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]soit située sur un serveur nommé **Serveur1**. Pour faire référence à cette table à partir d’un autre serveur, **Server2**, une application cliente devrait utiliser le nom en quatre parties **Server1.AdventureWorks.Person.Employee**. En outre, si l'emplacement de la table devait changer, par exemple vers un autre serveur, l'application cliente devrait être modifiée de façon à refléter ce changement.  
  
Pour faire face à ces deux situations, vous pouvez créer un synonyme, en l’occurrence **EmpTable**, sur le serveur **Server2** pour la table **Employee** située sur le serveur **Server1**. Maintenant, l’application cliente doit seulement utiliser le nom en une seule partie **EmpTable** pour référencer la table **Employee** . De même, si l’emplacement de la table **Employee** change, vous devez modifier le synonyme **EmpTable** de manière à ce qu’il pointe vers le nouvel emplacement de la table **Employee** . Étant donné qu’il n’existe pas d’instruction ALTER SYNONYM, vous devez d’abord supprimer le synonyme **EmpTable**, puis le recréer avec le même nom, mais en le faisant pointer vers le nouvel emplacement de la table **Employee**.  
  
Un synonyme est un objet appartenant à un schéma et, à ce titre, son nom doit être unique. Vous pouvez créer des synonymes pour les objets de base de données suivants :  

:::row:::
    :::column:::
        Procédure stockée d'un assembly (CLR)

        Fonction scalaire d'un assembly (CLR)

        Procédure de réplication et de filtrage

        Fonction scalaire SQL

        Fonction table inline SQL

        Affichage
    :::column-end:::
    :::column:::
        Fonction table d'un assembly (CLR)

        Fonctions d'agrégation d'un assembly (CLR)

        Fonction table SQL

        Procédure stockée SQL

        Table* (définie par l’utilisateur)
    :::column-end:::
:::row-end:::

*Comprend des tables temporaires locales et globales  
  
> [!NOTE]  
> Les noms en quatre parties des objets de base de fonction ne sont pas pris en charge.  
  
Un synonyme ne peut pas être l'objet de base d'un autre synonyme ni référencer une fonction d'agrégation définie par l'utilisateur.  
  
La liaison entre un synonyme et son objet de base se fait uniquement par le nom. Toute vérification d'existence, de type et d'autorisations sur l'objet de base est différée jusqu'à l'exécution. Par conséquent, l'objet de base peut être modifié, supprimé ou bien supprimé et remplacé par un autre objet portant le même nom que l'objet de base initial. Par exemple, prenons l’exemple d’un synonyme, **MesContacts**, qui référence la table **Person.Contact** dans [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]. Si la table **Contact** est supprimée, puis remplacée par une vue nommée **Person.Contact**, **MyContacts** référence la vue **Person.Contact** .  
  
Les références aux synonymes ne sont pas liées au schéma. Par conséquent, un synonyme peut être supprimé à tout moment. Toutefois, si vous supprimez un synonyme, vous courez le risque de laisser des références non résolues à celui-ci. Ces références ne sont trouvées qu'au moment de l'exécution.  
  
## <a name="synonyms-and-schemas"></a>Synonymes et schémas  
Si vous disposez d'un schéma par défaut qui ne vous appartient pas et que vous souhaitez créer un synonyme, vous devez qualifier le nom du synonyme avec le nom d'un schéma dont vous êtes propriétaire. Par exemple, si vous êtes propriétaire d’un schéma **x**, mais que **y** est votre schéma par défaut et que vous utilisez l’instruction CREATE SYNONYM, vous devez faire précéder le nom du synonyme du schéma **x**, au lieu d’attribuer au synonyme un nom en une seule partie. Pour plus d’informations sur la création de synonymes, consultez [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md).  
  
## <a name="granting-permissions-on-a-synonym"></a>Octroi d'autorisations sur un synonyme  
Seuls les propriétaires de synonymes, les membres de **db_owner** ou ceux de **db_ddladmin** peuvent accorder une autorisation sur un synonyme.  
  
Vous pouvez appliquer les instructions `GRANT`, `DENY` et `REVOKE` à tout ou partie des autorisations suivantes pour un synonyme :  

:::row:::
    :::column:::
      CONTROL

      Exécutez

      SELECT

      UPDATE
    :::column-end:::
    :::column:::
      Suppression

      INSERT

      TAKE OWNERSHIP

      VIEW DEFINITION
    :::column-end:::
:::row-end:::

## <a name="using-synonyms"></a>Utilisation de synonymes  
 Vous pouvez utiliser les synonymes à la place de leur objet de base référencé dans de nombreuses instructions SQL et leurs contextes d'expression. Les colonnes suivantes contiennent une liste de ces instructions et contextes d’expression :  

:::row:::
    :::column:::
        SELECT

        UPDATE

        Exécutez
    :::column-end:::
    :::column:::
        INSERT

        Suppression

        Sub-selects
    :::column-end:::
:::row-end:::
 
 Si vous travaillez avec des synonymes dans les contextes précédemment cités, l'objet de base est affecté. Par exemple, si un synonyme référence un objet de base qui est une table et que vous insérez une ligne dans le synonyme, vous insérez en fait une ligne dans la table référencée.  
  
> [!NOTE]  
> Vous ne pouvez pas référencer un synonyme situé sur un serveur lié.  
  
 Vous pouvez utiliser un synonyme en tant que paramètre de la fonction OBJECT_ID ; par contre, la fonction renvoie alors l'ID d'objet du synonyme, et non celui de l'objet de base.  
  
 Vous ne pouvez pas référencer un synonyme dans une instruction DDL. Par exemple, les instructions suivantes, qui référencent un synonyme nommé `dbo.MyProduct`, génèrent des erreurs :  
  
```sql  
ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null;  
EXEC ('ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null');  
```  
  
Les instructions d'autorisation suivantes sont associées uniquement au synonyme, et pas à l'objet de base :  

:::row:::
    :::column:::
        GRANT

        REVOKE
    :::column-end:::
    :::column:::
        DENY
    :::column-end:::
:::row-end:::

Les synonymes ne sont pas liés à un schéma et ne peuvent donc pas être référencés dans les contextes d'expression suivants qui sont liés à un schéma :  

:::row:::
    :::column:::
        Contraintes CHECK

        Expressions par défaut

        Vues liées à un schéma
    :::column-end:::
    :::column:::
        Colonnes calculées

        Expressions de règle

        Fonctions liées à un schéma
    :::column-end:::
:::row-end:::
  
Pour plus d’informations sur les fonctions liées au schéma, consultez [Créer des fonctions définies par l’utilisateur &#40;moteur de base de données&#41;](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md).  
  
## <a name="getting-information-about-synonyms"></a>Obtention d'informations sur les synonymes  
L'affichage catalogue `sys.synonyms` contient une entrée pour chaque synonyme dans une base de données déterminée. Cet affichage catalogue expose les métadonnées synonymes, telles que le nom du synonyme et celui de l'objet de base. Pour plus d’informations, consultez [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md).  
  
À l'aide des propriétés étendues, vous pouvez ajouter un texte descriptif ou instructif, des masques d'entrée et des règles de mise en forme comme propriétés d'un synonyme. Étant donné que la propriété est stockée dans la base de données, toutes les applications qui la lisent peuvent évaluer l'objet de la même manière. Pour plus d’informations, consultez [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md).  
  
Pour rechercher le type de base de l'objet de base d'un synonyme, utilisez la fonction OBJECTPROPERTYEX. Pour plus d’informations, consultez [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md).  
  
### <a name="examples"></a>Exemples  
L'exemple suivant retourne le type de base de l'objet de base d'un synonyme qui est un objet local.  
  
```sql  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee   
FOR AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyEmployee'), 'BaseType') AS BaseType;  
```  
  
L'exemple suivant retourne le type de base de l'objet de base d'un synonyme qui est un objet distant situé sur un serveur appelé `Server1`.  
  
```sql  
EXECUTE sp_addlinkedserver Server1;  
GO  
CREATE SYNONYM MyRemoteEmployee  
FOR Server1.AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyRemoteEmployee'), 'BaseType') AS BaseType;  
GO  
```  
  
## <a name="related-content"></a>Contenu associé  
 [Créer des synonymes](../../relational-databases/synonyms/create-synonyms.md)    
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md)    
 [DROP SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/drop-synonym-transact-sql.md)    
  
