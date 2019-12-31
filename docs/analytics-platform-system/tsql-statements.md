---
title: Instructions T-SQL
description: Instructions T-SQL pour le système de plateforme d’analyse (APS) SQL Server Parallel Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ce80d7a27384f628af02bfa58abcaa351b569d56
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399808"
---
# <a name="t-sql-statements-for-parallel-data-warehouse"></a>Instructions T-SQL pour les Data Warehouse parallèles
Instructions Transact-SQL (T-SQL) pour le système de plateforme d’analyse (APS) SQL Server Parallel Data Warehouse (PDW).

## <a name="data-definition-language-ddl-statements"></a>Instructions du langage de définition de données (DDL)
* [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)
* [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md)
* [ALTER PROCEDURE](../t-sql/statements/alter-procedure-transact-sql.md)
* [MODIFIER LE SCHÉMA](../t-sql/statements/alter-schema-transact-sql.md)
* [ALTER TABLE](../t-sql/statements/alter-table-transact-sql.md)
* [CRÉER UN INDEX COLUMNSTORE](../t-sql/statements/create-columnstore-index-transact-sql.md)
* [CRÉER UNE BASE DE DONNÉES](../t-sql/statements/create-database-azure-sql-data-warehouse.md)
* [CRÉER DES INFORMATIONS D’IDENTIFICATION ÉTENDUES À LA BASE DE DONNÉES](../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [CRÉER UNE SOURCE DE DONNÉES EXTERNE](../t-sql/statements/create-external-data-source-transact-sql.md)
* [CRÉER UN FORMAT DE FICHIER EXTERNE](../t-sql/statements/create-external-file-format-transact-sql.md)
* [CRÉER UNE TABLE EXTERNE](../t-sql/statements/create-external-table-transact-sql.md)
* [CRÉER UNE FONCTION](../t-sql/statements/create-function-sql-data-warehouse.md)
* [CRÉER UN INDEX](../t-sql/statements/create-index-transact-sql.md)
* [CRÉER UNE PROCÉDURE](../t-sql/statements/create-procedure-transact-sql.md)
* [CRÉER UN SCHÉMA](../t-sql/statements/create-schema-transact-sql.md)
* [CRÉER DES STATISTIQUES](../t-sql/statements/create-statistics-transact-sql.md)
* [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md)
* [CREATE TABLE COMME SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)
* [CRÉER UNE VUE](../t-sql/statements/create-view-transact-sql.md)
* [SUPPRIMER LA SOURCE DE DONNÉES EXTERNE](../t-sql/statements/drop-external-data-source-transact-sql.md)
* [SUPPRIMER LE FORMAT DE FICHIER EXTERNE](../t-sql/statements/drop-external-file-format-transact-sql.md)
* [SUPPRIMER LA TABLE EXTERNE](../t-sql/statements/drop-external-table-transact-sql.md)
* [DROP INDEX](../t-sql/statements/drop-index-transact-sql.md)
* [SUPPRIMER LA PROCÉDURE](../t-sql/statements/drop-procedure-transact-sql.md)
* [SUPPRIMER LES STATISTIQUES](../t-sql/statements/drop-statistics-transact-sql.md)
* [DROP TABLE](../t-sql/statements/drop-table-transact-sql.md)
* [SUPPRIMER LE SCHÉMA](../t-sql/statements/drop-schema-transact-sql.md)
* [SUPPRIMER LA VUE](../t-sql/statements/drop-view-transact-sql.md)
* [RENOMMER](../t-sql/statements/rename-transact-sql.md)
* [TRUNCATE TABLE](../t-sql/statements/truncate-table-transact-sql.md)
* [METTRE À JOUR LES STATISTIQUES](../t-sql/statements/update-statistics-transact-sql.md)

## <a name="data-manipulation-language-dml-statements"></a>Instructions du langage de manipulation de données
* [SUPPRIMER](../t-sql/statements/delete-transact-sql.md)
* [Insérer](../t-sql/statements/insert-transact-sql.md)
* [MISE À jour](../t-sql/queries/update-transact-sql.md)

## <a name="database-console-commands"></a>Commandes de la console de base de données
* [DBCC DROPCLEANBUFFERS](../t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql.md)
* [DBCC FREEPROCCACHE](https://msdn.microsoft.com/library/mt204018.aspx)
* [DBCC SHRINKLOG](https://msdn.microsoft.com/library/mt204020.aspx)
* [PDW_SHOWEXECUTIONPLAN DBCC](https://msdn.microsoft.com/library/mt204017.aspx)
* [PDW_SHOWPARTITIONSTATS DBCC](https://msdn.microsoft.com/library/mt204013.aspx)
* [PDW_SHOWSPACEUSED DBCC](../t-sql/database-console-commands/dbcc-pdw-showspaceused-transact-sql.md)
* [SHOW_STATISTICS DBCC](https://msdn.microsoft.com/library/mt204043.aspx)

## <a name="query-statements"></a>Instructions de requête
* [SÉLECTIONNÉ](../t-sql/queries/select-transact-sql.md)
* [AVEC common_table_expression](../t-sql/queries/with-common-table-expression-transact-sql.md)
* [EXCEPT et INTERSECT](../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)
* [EXPLAIN](../t-sql/queries/explain-transact-sql.md)
* [De](../t-sql/queries/from-transact-sql.md)
* [Utilisation de PIVOT et UNPIVOT](../t-sql/queries/from-using-pivot-and-unpivot.md)
* [REGROUPER PAR](../t-sql/queries/select-group-by-transact-sql.md)
* [HAVING](../t-sql/queries/select-having-transact-sql.md)
* [TRIER PAR](../t-sql/queries/select-order-by-clause-transact-sql.md)
* [OPTION](../t-sql/queries/option-clause-transact-sql.md)
* [UE](../t-sql/language-elements/set-operators-union-transact-sql.md)
* [Cela](../t-sql/queries/where-transact-sql.md)
* [TOP](../t-sql/queries/top-transact-sql.md)
* [Alias](../t-sql/queries/aliasing-azure-sql-data-warehouse-parallel-data-warehouse.md)
* [Condition de recherche](../t-sql/queries/search-condition-transact-sql.md)
* [Sous-requêtes](../t-sql/queries/subqueries-azure-sql-data-warehouse-parallel-data-warehouse.md)

## <a name="security-statements"></a>Instructions de sécurité
* Autorisations : [GRANT](../t-sql/statements/grant-transact-sql.md), [DENY](../t-sql/statements/deny-transact-sql.md), [REVOKE](../t-sql/statements/revoke-transact-sql.md)
* [MODIFIER L’AUTORISATION](../t-sql/statements/alter-authorization-transact-sql.md)
* [MODIFIER LE CERTIFICAT](../t-sql/statements/alter-certificate-transact-sql.md)
* [ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)
* [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md)
* [MODIFIER LA CLÉ PRINCIPALE](../t-sql/statements/alter-master-key-transact-sql.md)
* [MODIFIER LE RÔLE](../t-sql/statements/alter-role-transact-sql.md)
* [ALTER USER](../t-sql/statements/alter-user-transact-sql.md)
* [CERTIFICAT DE SAUVEGARDE](../t-sql/statements/backup-certificate-transact-sql.md)
* [FERMER LA CLÉ PRINCIPALE](../t-sql/statements/close-master-key-transact-sql.md)
* [CRÉER UN CERTIFICAT](../t-sql/statements/create-certificate-transact-sql.md)
* [CRÉER UNE CLÉ DE CHIFFREMENT DE BASE DE DONNÉES](../t-sql/statements/create-database-encryption-key-transact-sql.md)
* [CRÉER UNE CONNEXION](../t-sql/statements/create-login-transact-sql.md)
* [CRÉER UNE CLÉ PRINCIPALE](../t-sql/statements/create-master-key-transact-sql.md)
* [CRÉER UN RÔLE](../t-sql/statements/create-role-transact-sql.md)
* [CRÉER UN UTILISATEUR](../t-sql/statements/create-user-transact-sql.md)
* [SUPPRIMER LE CERTIFICAT](../t-sql/statements/drop-certificate-transact-sql.md)
* [SUPPRIMER LA CLÉ DE CHIFFREMENT DE BASE DE DONNÉES](../t-sql/statements/drop-database-encryption-key-transact-sql.md)
* [SUPPRIMER LA CONNEXION](../t-sql/statements/drop-login-transact-sql.md)
* [SUPPRIMER LA CLÉ PRINCIPALE](../t-sql/statements/drop-master-key-transact-sql.md)
* [SUPPRIMER LE RÔLE](../t-sql/statements/drop-role-transact-sql.md)
* [SUPPRIMER UN UTILISATEUR](../t-sql/statements/drop-user-transact-sql.md)
* [OUVRIR LA CLÉ PRINCIPALE](../t-sql/statements/open-master-key-transact-sql.md)

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations de référence, consultez [éléments de langage t-SQL](tsql-language-elements.md) et [vues système t-SQL](tsql-system-views.md).

<!--Image references-->

<!--Article references-->

<!--MSDN references-->

<!--Other Web references-->
