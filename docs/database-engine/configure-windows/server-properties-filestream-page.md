---
title: Propriétés de SQL Server (page FILESTREAM) | Microsoft Docs
description: Découvrez les paramètres FILESTREAM dans SQL Server. Découvrez comment activer FILESTREAM et comment configurer l’accès client distant et d’autres propriétés.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.filestream.f1
helpviewer_keywords:
- FILESTREAM [SQL Server], properties page
ms.assetid: 8a8d38d3-e97a-4b09-a40b-659b2e3a5c47
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 81edbd9bfc913f9d339625a993f866d44e1a313b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730926"
---
# <a name="server-properties---filestream-page"></a>Propriétés de SQL Server - page FILESTREAM
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilisez cette page pour activer FILESTREAM pour cette installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
 **Activer FILESTREAM pour l'accès Transact-SQL**  
 Sélectionnez cette option pour activer FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] . Ce contrôle doit être activé pour que les autres options de contrôle soient disponibles.  
  
 **Activer FILESTREAM pour l'accès en continu des E/S de fichier**  
 Sélectionnez cette option pour activer l'accès en continu Win32 pour FILESTREAM.  
  
 **Nom du partage Windows**  
 Utilisez ce contrôle pour entrer le nom du partage Windows dans lequel les données FILESTREAM doivent être stockées.  
  
 **Permettre aux clients distants d'avoir un accès en continu aux données FILESTREAM**  
 Sélectionnez ce contrôle pour permettre aux clients distants d'accéder à ces données FILESTREAM sur ce serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
