---
title: Nom de canal nommé non valide peut bloquer la mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dddd5da66f09226579a6366baa1a16a6ab00d6bf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094191"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Un nom de canal nommé non valide peut bloquer la mise à niveau
  La mise à niveau échoue si le protocole des canaux nommés est configuré de manière incorrecte.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Pendant la mise à niveau, le programme d’installation démarre le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance avec prise en charge de la mémoire partagée, un canal nommé qui accepte uniquement les connexions locales. Si le nom du canal spécifié sur le serveur n’est pas vide, il doit commencer par la chaîne «\\\\. \pipe\\» soit valide. Si le nom de canal n'est pas valide, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne démarre pas et l'installation échoue.  
  
## <a name="corrective-action"></a>Action corrective  
 Utilisez le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilitaire réseau** pour fournir un nom de canal valide, puis exécutez le programme d’installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
