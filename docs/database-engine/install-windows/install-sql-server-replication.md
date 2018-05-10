---
title: Installer la réplication SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: install
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
caps.latest.revision: 41
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b9d0fd5b246734a73293a16ff449e237ab799d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="install-sql-server-replication"></a>Installer la réplication SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Les composants de réplication peuvent être installés à l'aide de l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à l'invite de commandes. Installez la réplication lors de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou lors de la modification d'une instance existante.  
  
Une fois que les composants de réplication sont installés, vous devez configurer le serveur avant de pouvoir utiliser la réplication. Pour plus d’informations, consultez [Configurer la distribution](../../relational-databases/replication/configure-distribution.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
>[!IMPORTANT]  
>Si vous installez des composants de réplication lorsque vous modifiez une instance existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez arrêter et redémarrer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une fois l'installation terminée. Cette action garantit que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reconnaît les sous-systèmes de l'agent de réplication et peut appeler les agents de réplication à partir des étapes de travail.  
  
## <a name="installing-replication-by-using-setup"></a>Installation de la réplication à l’aide du programme d’installation  
**Pour installer la réplication en même temps qu’une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
- Pour installer les composants de réplication, notamment des objets RMO (Replication Management Objects), sélectionnez **Réplication SQL Server** dans la page **Sélection de composant** de l’Assistant Installation.  
  
## <a name="installing-replication-from-the-command-prompt"></a>Installation de la réplication à partir de l'invite de commandes  
 **Pour installer la réplication en même temps qu’une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
- Voir [Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server](../../database-engine/install-windows/install-sql-server.md)   
 [Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server](../../sql-server/editions-and-components-of-sql-server-2017.md)  
  
  
