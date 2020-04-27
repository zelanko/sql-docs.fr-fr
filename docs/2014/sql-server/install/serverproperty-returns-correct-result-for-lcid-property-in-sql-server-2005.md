---
title: SERVERPROPERTY retourne un résultat correct pour la propriété LCID dans SQL Server 2005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 24bb31759ba520f26b8e9af3a6533d8f0feebbe0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092240"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SERVERPROPERTY retourne un résultat correct pour la propriété LCID dans SQL Server 2005
  Lorsque l'instruction SERVERPROPERTY('LCID') est exécutée sur des serveurs de classement binaire, la fonction retourne l'identificateur Windows local (LCID) qui correspond au classement du serveur.  
  
> [!NOTE]  
>  Pour les fichiers de commandes et de trace qui contiennent des références à SERVERPROPERTY ("LCID") et sont exécutés sur d'autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le Conseiller de mise à niveau détecte ce changement de comportement uniquement si les autres instances possèdent le même classement que l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les applications pour qu'elles attendent que l'instruction SERVERPROPERTY ("LCID") retourne l'identificateur LCID Windows qui correspond au classement du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
