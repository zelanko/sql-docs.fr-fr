---
title: POUR parcourir n’est pas autorisée dans les vues en mode de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ccd82fd7b971c97319daa480ba3f9a222d026280
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065509"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a>L'option FOR BROWSE n'est pas autorisée dans les vues en mode de compatibilité 90 ou ultérieur
  Le Conseiller de mise à niveau a détecté qu'une vue est définie à l'aide de la clause FOR BROWSE. La clause FOR BROWSE est autorisée (et ignorée) dans les vues lorsque le mode de compatibilité de la base de données est défini à 80. Elle n'est pas autorisée dans les vues si le mode de compatibilité de la base de données est défini à 90 ou ultérieur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Avant de définir le mode de compatibilité de la base de données à 90 ou ultérieur, supprimez la clause FOR BROWSE des définitions de vues. Pour plus d'informations, consultez « sp_dbcmptlevel » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
