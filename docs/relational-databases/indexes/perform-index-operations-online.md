---
description: Exécuter des opérations en ligne sur les index
title: Exécuter des opérations en ligne sur les index | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.prod_service: table-view-index, sql-database
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c8bb42554935076679107d78ee5c2eed0b838797
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470439"
---
# <a name="perform-index-operations-online"></a>Exécuter des opérations en ligne sur les index
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Cette rubrique explique comment créer, reconstruire ou supprimer des index en ligne dans [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option ONLINE permet l'accès simultané des utilisateurs aux tables sous-jacentes ou aux données des index cluster et aux index non-cluster associés pendant ces opérations sur les index. Par exemple, pendant qu'un index cluster est reconstruit par un utilisateur, cet utilisateur et d'autres peuvent continuer de mettre à jour et d'interroger les données sous-jacentes. Lorsque vous effectuez des opérations DDL (Data Definition Language) en mode hors connexion, comme la construction ou la reconstruction d'un index cluster, ces opérations posent des verrous exclusifs sur les données sous-jacentes et les index associés. Ces verrous empêchent toute modification et toute interrogation des données sous-jacentes jusqu'à la fin de l'opération effectuée sur l'index.  
  
> [!NOTE]  
>  Les opérations d'index en ligne ne sont pas disponibles dans toutes les édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Éditions et fonctionnalités prises en charge de SQL Server](../../sql-server/editions-and-components-of-sql-server-version-15.md). 
>
> Les opérations d’index en ligne sont disponibles dans Azure SQL Database.
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour reconstruire un index en ligne à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Il est recommandé d'effectuer les opérations sur les index en ligne dans les environnements qui sont opérationnels 24 heures sur 24 et 7 jours sur 7, dans lesquels il est vital de maintenir l'accès des utilisateurs.  
  
-   L'option ONLINE peut être utilisée dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes.  
  
    -   [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)  
  
    -   [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)  
  
    -   [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)  
  
    -   [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) (Pour ajouter ou supprimer des contraintes UNIQUE ou PRIMARY KEY avec l’option d’index CLUSTERED)  
  
-   Pour plus d’informations sur les limitations et les restrictions de création, reconstruction ou suppression d’index en ligne, consultez [Instructions pour les opérations d’index en ligne](../../relational-databases/indexes/guidelines-for-online-index-operations.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-rebuild-an-index-online"></a>Pour reconstruire un index en ligne  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer la base de données qui contient la table sur laquelle vous souhaitez reconstruire un index en ligne.  
  
2.  Développez le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table sur laquelle vous souhaitez reconstruire un index en ligne.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index à reconstruire en ligne, puis sélectionnez **Propriétés**.  
  
6.  Sous **Sélectionner une page**, sélectionnez **Options**.  
  
7.  Sélectionnez **Autoriser le traitement des instructions DML en ligne**, puis sélectionnez **True** dans la liste.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez avec le bouton droit sur l’index à reconstruire en ligne, puis sélectionnez **Reconstruire**.  
  
10. Dans la boîte de dialogue **Reconstruire les index** , vérifiez que l'index correct figure dans la grille **Index à reconstruire** , puis cliquez sur **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
### <a name="to-create-rebuild-or-drop-an-index-online"></a>Pour créer, reconstruire ou supprimer un index en ligne  
  
L’exemple suivant reconstruit un index en ligne existant dans la base de données AdventureWorks.

```sql
ALTER INDEX AK_Employee_NationalIDNumber
    ON HumanResources.Employee
    REBUILD WITH (ONLINE = ON);
```  
  
L'exemple suivant supprime un index cluster en ligne et déplace la table résultante (segment de mémoire) vers le groupe de fichiers `NewGroup` en utilisant la clause `MOVE TO` . Les affichages catalogue `sys.indexes`, `sys.tables`et `sys.filegroups` sont interrogés pour vérifier le placement de l'index et de la table dans les groupes de fichiers avant et après l'opération de déplacement.  
  
[!code-sql[IndexDDL#DropIndex4](../../relational-databases/indexes/codesnippet/tsql/perform-index-operations_1.sql)]  

Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).

## <a name="next-steps"></a>Étapes suivantes

- [Considérations relatives aux index pouvant être repris](guidelines-for-online-index-operations.md#resumable-index-considerations)
