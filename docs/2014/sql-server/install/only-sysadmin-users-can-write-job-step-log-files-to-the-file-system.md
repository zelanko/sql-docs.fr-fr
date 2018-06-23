---
title: Seuls les utilisateurs sysadmin peuvent écrire des fichiers de journal des étapes de travail pour le système de fichiers | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e0b7638bbbf33cdd820467cd21edc40a6f5c42ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052978"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>Seuls les utilisateurs sysadmin peuvent écrire des fichiers journaux des étapes de travail dans le système de fichiers
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] écrit éventuellement un journal pour chaque étape de travail.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut écrire des journaux dans le système de fichiers pour les travaux qui sont détenus par les membres de la **sysadmin** rôle serveur fixe. Si le propriétaire du travail n’est pas un membre de la **sysadmin** rôle et si le compte proxy est activé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut écrire des journaux dans le système de fichiers en utilisant les informations d’identification du compte proxy.  
  
 Une fois que vous mettez à niveau, les travaux qui sont détenus par les utilisateurs qui ne sont pas membres de la **sysadmin** rôle serveur fixe ne peut plus écrire des journaux dans le système de fichiers. Au lieu de cela, ces utilisateurs peuvent sélectionner l’option pour écrire les journaux à une table dans le **msdb** base de données. Membres de la **sysadmin** rôle peut encore écrire des fichiers journaux dans le système de fichiers.  
  
## <a name="corrective-action"></a>Action corrective  
 Une fois que vous mettez à niveau, les travaux qui sont détenus par les utilisateurs qui ne sont pas membres de la **sysadmin** rôle continuera à s’exécuter, mais les journaux ne seront pas créés. Pour consigner les étapes de travail dans une table, les utilisateurs qui ne sont pas membres de la **sysadmin** rôle doit mettre à jour manuellement leurs tâches.  
  
 Pour plus d'informations, consultez les rubriques « Création de travaux », « Création d'étapes de travail » et « Gestion de plusieurs étapes de travail » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  