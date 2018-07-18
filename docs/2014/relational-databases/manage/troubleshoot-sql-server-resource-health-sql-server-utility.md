---
title: Résoudre les problèmes de contrôle d’intégrité de SQL Server (utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 743186343c288b4ea49255acb5651c6b4716173c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219239"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Résoudre les problèmes de contrôle d'intégrité de SQL Server (Utilitaire SQL Server)
  La résolution des problèmes d'intégrité des ressources identifiés par un UCP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure l'atténuation de l'UC surexploitée sur un ordinateur ou sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou atténuer l'UC surexploitée pour une application de la couche Données. D'autres problèmes peuvent inclure la résolution de l'espace de fichier surexploité pour les fichiers de base de données ou la résolution de la surexploitation d'espace disque alloué sur un volume de stockage.  
  
 Notez que si la base de données se trouve dans l'état « urgence », l'état d'intégrité affiche l'espace de fichier journal surexploité.  
  
 Pour plus d’informations sur l’échec de la collecte de données qui provoque des icônes d’état grises en mode Liste d’instances gérées sur un UCP, consultez [Résolution des problèmes liés à l’utilitaire SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md). Pour plus d’informations sur la prise en main de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](sql-server-utility-features-and-tasks.md).  
  
 Pour plus d'informations sur l'atténuation de problèmes d'intégrité des ressources spécifiques identifiés par un UCP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, consultez les rubriques suivantes :  
  
-   [Comment identifier la version et l'édition de votre SQL Server](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Résolution des problèmes de performances dans SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
