---
title: SERVERPROPERTY retourne un résultat correct pour la propriété LCID dans SQL Server 2005 | Documents Microsoft
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
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b0179ebe39b56082bc51cfe944e6de28e0b4a2c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143412"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SERVERPROPERTY retourne un résultat correct pour la propriété LCID dans SQL Server 2005
  Lorsque l'instruction SERVERPROPERTY('LCID') est exécutée sur des serveurs de classement binaire, la fonction retourne l'identificateur Windows local (LCID) qui correspond au classement du serveur.  
  
> [!NOTE]  
>  Pour les fichiers de commandes et de trace qui contiennent des références à SERVERPROPERTY ("LCID") et sont exécutés sur d'autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le Conseiller de mise à niveau détecte ce changement de comportement uniquement si les autres instances possèdent le même classement que l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les applications pour qu'elles attendent que l'instruction SERVERPROPERTY ("LCID") retourne l'identificateur LCID Windows qui correspond au classement du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
