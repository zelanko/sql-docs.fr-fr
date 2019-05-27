---
title: Configuration du Winsock Proxy ne pas pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Winsock proxy configuration [SQL Server]
ms.assetid: abf71f7b-8bd7-49d2-92f7-9ddf72924d8c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e7d5daa8042e53b9bf26ad507c4be1f361821909
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66090976"
---
# <a name="winsock-proxy-configuration-not-supported"></a>La configuration du proxy WinSock n'est pas prise en charge
  Le proxy Winsock ne peut pas être configuré à l’aide de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outils.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les outils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas configurer les composants Windows.  
  
## <a name="corrective-action"></a>Action corrective  
 Utilisez Microsoft Internet Security and Acceleration Server (ISA) pour publier un ordinateur. Pour des informations sur la configuration du proxy Winsock, consultez la documentation de votre serveur proxy.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
