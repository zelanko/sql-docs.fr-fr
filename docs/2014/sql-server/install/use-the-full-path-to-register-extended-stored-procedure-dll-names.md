---
title: Utiliser le chemin d’accès complet pour inscrire les noms de DLL de procédure stockée étendue | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ec4ef3fc2e0f2c4834ffa7479a00562ae15d07f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058830"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>Utiliser le chemin d'accès complet pour inscrire les noms de DLL de procédures stockées étendues
  Les procédures stockées étendues qui étaient auparavant inscrites sans le chemin d'accès complet pour le nom de la DLL risquent de ne pas fonctionner dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les procédures stockées étendues qui étaient auparavant inscrites sans le chemin d'accès complet pour le nom de la DLL risquent de ne pas fonctionner après la mise à niveau. Ceci est dû au fait que l'ancien répertoire BINN n'est pas ajouté au nouveau chemin durant le processus de mise à niveau. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risque de ne pas pouvoir localiser les procédures stockées étendues.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant d'effectuer la mise à niveau, exécutez la procédure suivante pour chaque procédure stockée étendue qui n'a pas été inscrite avec un nom de chemin complet :  
  
1.  Exécutez sp_dropextendedproc pour supprimer la procédure stockée étendue.  
  
2.  Exécutez sp_addextendedproc pour inscrire la procédure stockée étendue avec le nom de chemin complet.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
