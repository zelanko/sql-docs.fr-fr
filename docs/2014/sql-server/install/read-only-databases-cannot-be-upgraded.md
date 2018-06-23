---
title: Bases de données en lecture seule ne peut pas être mis à niveau | Documents Microsoft
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
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 11f94ceed205d8984ed5a253e1d989211012f10f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154783"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Les bases de données en lecture seule ne peuvent pas être mises à niveau
  Le Conseiller de mise à niveau a déterminé que certaines bases de données sur cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas être mises à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Une base de données en lecture seule a été détectée. Le programme d'installation doit pouvoir écrire dans la base de données pour la mettre à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque personne n’utilise la base de données, utilisez la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ou l’instruction ALTER DATABASE pour modifier la base de données en lecture-écriture. L'instruction suivante affecte à la base de données l'attribut lecture-écriture.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Pour plus d'informations sur l'instruction ALTER DATABASE, consultez la rubrique « ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)]) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
