---
description: DDL, fonctions, procédures stockées et vues FileTable
title: Fonctions, procédures stockées, vues FileTable | Microsoft Docs
descriptions: Learn which Transact-SQL statements and which SQL Server functions, stored procedures, and views have been added or changed to support the FileTable feature.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f1736422ff6ff81a7e48931b390acc710abf41b3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448941"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>DDL, fonctions, procédures stockées et vues FileTable

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Répertorie les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] et les objets de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ont été ajoutés ou modifiés afin de prendre en charge la fonctionnalité FileTable dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La colonne d'état dans les tableaux suivants indique si l'élément est nouveau dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ou bien s'il était présent dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais a été modifié dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour prendre en charge la recherche sémantique.  
  
 Pour obtenir la liste des instructions et des objets de base de données qui prennent en charge FILESTREAM, consultez [FILESTREAM DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filestream-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Instructions DDL (Data Definition Language, langage de définition de données) Transact-SQL  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)<br /><br /> [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)|Modifié|[Activer les conditions préalables pour les FileTables](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)<br /><br /> [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|Modifié|[Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)|Modifié|[Activer les conditions préalables pour les FileTables](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|Modifié|[Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)<br /><br /> [Arguments RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Modifié||  
  
##  <a name="functions"></a><a name="func"></a> Fonctions  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](../../relational-databases/system-functions/filetablerootpath-transact-sql.md)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getfilenamespacepath-transact-sql.md)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="stored-procedures"></a><a name="sproc"></a> Procédures stockées  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)|**Ajouté**|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="catalog-views"></a><a name="cv"></a> Affichages catalogue  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)|**Ajouté**|[Activer les conditions préalables pour les FileTables](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)|**Ajouté**|[Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)|**Ajouté**|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)|Modifié|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="dynamic-management-views"></a><a name="dmv"></a> Vues de gestion dynamique  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)|**Ajouté**|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  
