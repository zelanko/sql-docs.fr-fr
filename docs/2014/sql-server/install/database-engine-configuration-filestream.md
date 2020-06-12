---
title: Configuration de la Moteur de base de données-FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53eb4eb049bfe700a83d58e05a3af1ee4f6f41a6
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83859699"
---
# <a name="database-engine-configuration---filestream"></a>Configuration du moteur de base de données - Filestream
  Utilisez cette page pour activer FILESTREAM pour cette installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. FILESTREAM intègre le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] avec un système de fichiers NTFS en stockant les `varbinary(max)` données BLOB (Binary Large Object) en tant que fichiers sur le système de fichiers. Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] peuvent insérer, mettre à jour, interroger, rechercher et sauvegarder des données FILESTREAM. Les interfaces de système de fichiers Win32 fournissent l'accès de diffusion en continu aux données.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
 **Activer FILESTREAM pour l’accès Transact-SQL**  
 Sélectionnez cette option pour activer FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] . Ce contrôle doit être activé pour que les autres options de contrôle soient disponibles.  
  
 **Activer FILESTREAM pour l’accès en continu d’e/s de fichier**  
 Sélectionnez cette option pour activer l'accès en continu Win32 pour FILESTREAM.  
  
 **Nom du partage Windows**  
 Utilisez ce contrôle pour entrer le nom du partage Windows dans lequel les données FILESTREAM doivent être stockées.  
  
 **Autoriser les clients distants à avoir un accès en continu aux données FILESTREAM**  
 Sélectionnez ce contrôle pour permettre aux clients distants d'accéder à ces données FILESTREAM sur ce serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Activer et configurer FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
