---
title: Seuls les utilisateurs sysadmin peuvent écrire des fichiers journaux d’étapes de travail dans le système de fichiers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84d04729e2f4c00c5d127a706727567c44855cd6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093678"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Seuls les utilisateurs sysadmin peuvent écrire des fichiers journaux des étapes de travail dans le système de fichiers
  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] écrit éventuellement un journal pour chaque étape de travail.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent peut écrire des journaux dans le système de fichiers pour les travaux qui sont détenus par les membres du rôle serveur fixe **sysadmin** . Si le propriétaire du travail n’est pas membre du rôle **sysadmin** et si le compte proxy est activé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent peut écrire des journaux dans le système de fichiers en utilisant les informations d’identification du compte proxy.  
  
 Après la mise à niveau, les travaux qui sont détenus par des utilisateurs qui ne sont pas membres du rôle serveur fixe **sysadmin** ne peuvent plus écrire de journaux dans le système de fichiers. Au lieu de cela, ces utilisateurs peuvent sélectionner l’option permettant d’écrire leurs journaux dans une table de la base de données **msdb** . Les membres du rôle **sysadmin** peuvent toujours écrire des fichiers journaux dans le système de fichiers.  
  
## <a name="corrective-action"></a>Action corrective  
 Après la mise à niveau, les travaux qui sont détenus par des utilisateurs qui ne sont pas membres du rôle **sysadmin** continuent à s’exécuter, mais les journaux ne seront pas créés. Pour consigner des étapes de travail dans une table, les utilisateurs qui ne sont pas membres du rôle **sysadmin** doivent mettre à jour manuellement leurs travaux.  
  
 Pour plus d'informations, consultez les rubriques « Création de travaux », « Création d'étapes de travail » et « Gestion de plusieurs étapes de travail » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de l'Agent SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
