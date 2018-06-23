---
title: AVEC des lignes n’est pas pris en charge dans les instructions CREATE STATISTICS dans le mode de compatibilité 90 ou ultérieur | Documents Microsoft
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
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d509352d99cab9359e7ea222f5fb2d5d7e28075
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139714"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>La clause WITH ROWS n'est pas prise en charge dans les instructions CREATE STATISTICS en mode de compatibilité 90 ou ultérieur
  La spécification de la clause WITH ROWS dans les instructions CREATE STATISTICS n'est pas prise en charge lorsque vous exécutez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de compatibilité 90 ou ultérieur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les instructions CREATE STATISTICS qui incluent WITH ROWS en spécifiant WITH SAMPLE *nombre* lignes, ou en spécifiant les autres options compatibles avec la syntaxe documentée. Pour plus d’informations, consultez la rubrique « CREATE STATISTICS (Transact-SQL) dans la documentation en ligne SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
