---
description: Déplacer des fichiers de bases de données
title: Déplacer des fichiers de bases de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa8fe0e721bbe571cf1f47d95bfdd79029059846
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194305"
---
# <a name="move-database-files"></a>Déplacer des fichiers de bases de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez déplacer les bases de données système et utilisateur en spécifiant le nouvel emplacement des fichiers dans la clause FILENAME de l’instruction [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md). Cette méthode peut être appliquée aux fichiers de données, aux fichiers journaux et aux fichiers de catalogues de texte intégral. Elle peut être utile dans les cas suivants :  
  
-   Récupération après défaillance. Par exemple, la base de données est en mode suspect ou a été fermée en raison d'une défaillance matérielle.  
  
-   Déplacement prévu.  
  
-   Déplacement en vue d'une maintenance de disque planifiée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Déplacer des bases de données utilisateur](../../relational-databases/databases/move-user-databases.md)|Décrit les procédures permettant de déplacer les fichiers de base de données utilisateur et les fichiers de catalogue de texte intégral vers un nouvel emplacement.|  
|[Déplacer des bases de données système](../../relational-databases/databases/move-system-databases.md)|Décrit les procédures permettant de déplacer les fichiers de base de données système vers un nouvel emplacement.|  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
