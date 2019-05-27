---
title: DDL, fonctions, procédures stockées et vues FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85e0c761f5dc784698b3aed361ce50488a93e366
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010102"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>DDL, fonctions, procédures stockées et vues FileTable
  Répertorie les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] et les objets de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ont été ajoutés ou modifiés afin de prendre en charge la fonctionnalité FileTable dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La colonne d'état dans les tableaux suivants indique si l'élément est nouveau dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ou bien s'il était présent dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais a été modifié dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour prendre en charge la recherche sémantique.  
  
 Pour obtenir la liste des instructions et des objets de base de données qui prennent en charge FILESTREAM, consultez [FILESTREAM DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="ddl"></a> Instructions DDL (Data Definition Language, langage de définition de données) Transact-SQL  
  
|Object|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)<br /><br /> [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)|Modifié|[Activer les conditions préalables pour les FileTables](enable-the-prerequisites-for-filetable.md)<br /><br /> [Gérer des FileTables](manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)|Modifié|[Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)|Modifié|[Activer les conditions préalables pour les FileTables](enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)|Modifié|[Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)<br /><br /> [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)|Modifié||  
  
##  <a name="func"></a> Fonctions  
  
|Object|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|**Ajouté**|[Travailler avec des répertoires et des chemins d'accès dans FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|**Ajouté**|[Travailler avec des répertoires et des chemins d'accès dans FileTables](work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="sproc"></a> Procédures stockées  
  
|Object|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)|**Ajouté**|[Gérer des FileTables](manage-filetables.md)|  
  
##  <a name="cv"></a> Affichages catalogue  
  
|Object|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)|**Ajouté**|[Activer les conditions préalables pour les FileTables](enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)|**Ajouté**|[Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)|**Ajouté**|[Gérer des FileTables](manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Modifié|[Gérer des FileTables](manage-filetables.md)|  
  
##  <a name="dmv"></a> Vues de gestion dynamique  
  
|Object|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)|**Ajouté**|[Gérer des FileTables](manage-filetables.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des FileTables](manage-filetables.md)  
  
  
