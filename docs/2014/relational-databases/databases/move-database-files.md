---
title: Déplacer des fichiers de bases de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 5491f3c4dfd47cac4047d0409c78001be80d6f13
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965830"
---
# <a name="move-database-files"></a>Déplacer des fichiers de bases de données
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez déplacer les bases de données système et utilisateur en spécifiant le nouvel emplacement des fichiers dans la clause FILENAME de l’instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) . Cette méthode peut être appliquée aux fichiers de données, aux fichiers journaux et aux fichiers de catalogues de texte intégral. Elle peut être utile dans les cas suivants :  
  
-   Récupération après défaillance. Par exemple, la base de données est en mode suspect ou a été fermée en raison d'une défaillance matérielle.  
  
-   Déplacement prévu.  
  
-   Déplacement en vue d'une maintenance de disque planifiée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Déplacer des bases de données utilisateur](move-user-databases.md)|Décrit les procédures permettant de déplacer les fichiers de base de données utilisateur et les fichiers de catalogue de texte intégral vers un nouvel emplacement.|  
|[Déplacer des bases de données système](system-databases.md)|Décrit les procédures permettant de déplacer les fichiers de base de données système vers un nouvel emplacement.|  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)  
  
  
