---
title: MSSQLSERVER_3169 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 57a63d884dabb1ad2e0e5d8b13dea4190dfa65de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62868913"
---
# <a name="mssqlserver3169"></a>MSSQLSERVER_3169
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3169|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|N/A|  
|Texte du message|La base de données a été sauvegardée sur un serveur exécutant la version %ls. Cette version est incompatible avec ce serveur, qui exécute la version %ls. Restaurez la base de données sur un serveur qui prend en charge la sauvegarde ou utilisez une sauvegarde compatible avec ce serveur.|  
  
## <a name="explanation"></a>Explication  
 Certaines fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affectent la structure des fichiers de base de données. Lorsque vous restaurez une base de données dans une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le format de fichier peut ne pas être compatible avec une autre version du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Par exemple, cette erreur peut se produire si vous utilisez le format de stockage vardecimal dans une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis que vous essayez de restaurer les fichiers de base de données dans une version antérieure à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Identifiez la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécute sur le serveur d'origine. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], soit cliquez sur le serveur, puis cliquez sur **propriétés** ou type `SELECT @@VERSION` dans une fenêtre de requête. Ouvrez la base de données en utilisant la version d'origine de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Examinez les fonctionnalités qui sont activées sur la base de données d'origine dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Modifiez ces paramètres de façon à utiliser la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle la base de données sera restaurée.  
  
  
