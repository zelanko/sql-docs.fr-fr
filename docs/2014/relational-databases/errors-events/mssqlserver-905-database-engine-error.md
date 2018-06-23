---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d84961f4903ac6dd0a950ceaa8a8fb9368efcf6d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053524"
---
# <a name="mssqlserver905"></a>MSSQLSERVER_905
    
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
 La base de données contient un ou plusieurs index ou tables partitionnés. Cette édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas utiliser le partitionnement. Par conséquent, la base de données ne peut pas être démarrée correctement. Les tables et les index partitionnés ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Détachez la base de données à l'aide de la procédure stockée sp_detach_db. Déplacez les fichiers, si nécessaire, puis attachez la base de données à une instance d’une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prise en charge en utilisant CREATE DATABASE avec l’option FOR ATTACH ou FOR ATTACH_REBUILD_LOG. Désactivez le partitionnement sur toutes les tables et supprimez les fonctions de partitionnement. Détachez encore la base de données et rattachez-la au serveur actif.  
  
  