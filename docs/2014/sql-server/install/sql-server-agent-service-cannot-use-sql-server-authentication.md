---
title: Service SQL Server Agent ne peut pas utiliser l’authentification SQL Server | Documents Microsoft
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
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ddda041de230fb13e2f743edc2c3867f9716c180
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154093"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Le service SQL Server Agent ne peut pas utiliser l'authentification SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prend en charge uniquement l'authentification Windows lorsque le service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent se connecte à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut uniquement se connecter à la base de données en utilisant l'authentification Windows. Cela signifie que le compte du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour plus d'informations, consultez les rubriques « Sécurité pour l'administration automatique » et « Implémentation de la sécurité de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  