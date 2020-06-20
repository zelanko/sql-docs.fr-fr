---
title: Le service SQL Server Agent ne peut pas utiliser l’authentification SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036252"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a>Le service SQL Server Agent ne peut pas utiliser l'authentification SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prend en charge uniquement l'authentification Windows lorsque le service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent se connecte à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut uniquement se connecter à la base de données en utilisant l'authentification Windows. Cela signifie que le compte du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour plus d'informations, consultez les rubriques « Sécurité pour l'administration automatique » et « Implémentation de la sécurité de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de l'Agent SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
