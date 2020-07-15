---
title: Résoudre les problèmes de contrôle d’intégrité de SQL Server (utilitaire SQL Server) | Microsoft Docs
description: Découvrez comment résoudre les problèmes liés à l’intégrité des ressources identifiés par SQL Server UCP, par exemple la sur-utilisation du processeur, de l’espace de fichier ou de l’espace disque alloué.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cb188aa5a71ef9631aa61ead08cfc33ed1210c7f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786449"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Résoudre les problèmes de contrôle d'intégrité de SQL Server (Utilitaire SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La résolution des problèmes d'intégrité des ressources identifiés par un UCP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure l'atténuation de l'UC surexploitée sur un ordinateur ou sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou atténuer l'UC surexploitée pour une application de la couche Données. D'autres problèmes peuvent inclure la résolution de l'espace de fichier surexploité pour les fichiers de base de données ou la résolution de la surexploitation d'espace disque alloué sur un volume de stockage.  
  
 Notez que, si une base de données se trouve dans l’état « urgence », l’état d’intégrité affiche l’espace de fichier journal surexploité.  
  
 Pour plus d’informations sur l’échec de la collecte de données qui provoque des icônes d’état grises en mode Liste d’instances gérées sur un UCP, consultez [Résolution des problèmes liés à l’utilitaire SQL Server](https://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453). Pour plus d’informations sur la prise en main de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Pour plus d'informations sur l'atténuation de problèmes d'intégrité des ressources spécifiques identifiés par un UCP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, consultez les rubriques suivantes :  
  
-   [Comment identifier la version et l'édition de votre SQL Server](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Résolution des problèmes de performances dans SQL Server 2008](https://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
