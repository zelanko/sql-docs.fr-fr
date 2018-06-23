---
title: Nom de canal nommé non valide peut bloquer la mise à niveau | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c94c1eeff18bff698e2a6353e29b72dd33278d03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043293"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Un nom de canal nommé non valide peut bloquer la mise à niveau
  La mise à niveau échoue si le protocole des canaux nommés est configuré de manière incorrecte.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Au cours de la mise à niveau, le programme d’installation démarre le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance avec prise en charge de la mémoire partagée, un canal nommé qui accepte uniquement les connexions locales. Si le nom de canal spécifié sur le serveur n’est pas vide, il doit commencer par la chaîne «\\\\. \pipe\\» soit valide. Si le nom de canal n'est pas valide, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne démarre pas et l'installation échoue.  
  
## <a name="corrective-action"></a>Action corrective  
 Utilisez le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilitaire réseau** pour fournir un nom de canal valide, puis exécutez le programme d’installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
