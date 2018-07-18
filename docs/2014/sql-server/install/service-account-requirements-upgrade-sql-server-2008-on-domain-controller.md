---
title: Conditions requises pour la mise à niveau vers SQL Server 2008 sur un contrôleur de domaine le compte de service | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cc2ec39bee7f9a64d75ccf4753220f69693155b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301659"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>Conditions requises par le compte de service pour la mise à niveau vers SQL Server 2008 sur un contrôleur de domaine
  Conseiller de mise à niveau a détecté une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours d’exécution sous un compte de Service réseau ou Service Local un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] contrôleur de domaine. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé sur un contrôleur de domaine [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas être exécutés avec les privilèges d'un compte de service local ou d'un compte de service réseau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Assurez-vous que tous les comptes de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont assignés à des comptes de domaine ou des comptes système locaux. Si cette modification n'est pas apportée avant la mise à niveau le programme d'installation se bloque. Les comptes de service SQL Writer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les services Active Directory Helper sont des exceptions car ils sont codés en dur dans le compte de service réseau et ne peuvent pas être modifiés.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
