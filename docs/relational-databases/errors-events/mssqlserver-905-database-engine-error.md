---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 648f373a5e1054ae72a462914072391f5560dce0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|905|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBSTARTUP_EE_PARTITIONING|  
|Texte du message|La base de données '%.*ls' ne peut pas être démarrée dans cette édition de SQL Server, car elle contient une fonction de partition '%.\*ls'. Seule l'édition Entreprise de SQL Server prend en charge le partitionnement.|  
  
## <a name="explanation"></a>Explication  
La base de données contient un ou plusieurs index ou tables partitionnés. Cette édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas utiliser le partitionnement. Par conséquent, la base de données ne peut pas être démarrée correctement. Les tables et les index partitionnés ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
Détachez la base de données à l'aide de la procédure stockée sp_detach_db. Déplacez les fichiers, si nécessaire, puis attachez la base de données à une instance d’une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prise en charge en utilisant CREATE DATABASE avec l’option FOR ATTACH ou FOR ATTACH_REBUILD_LOG. Désactivez le partitionnement sur toutes les tables et supprimez les fonctions de partitionnement. Détachez encore la base de données et rattachez-la au serveur actif.  
  
