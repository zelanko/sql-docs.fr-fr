---
title: MSSQLSERVER_3169 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 06a81eaa83b3420912494b61135790c4e8fabe29
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68039295"
---
# <a name="mssqlserver_3169"></a>MSSQLSERVER_3169
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|3169|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|N/D|  
|Texte du message|La base de données a été sauvegardée sur un serveur exécutant la version %ls. Cette version est incompatible avec ce serveur, qui exécute la version %ls. Restaurez la base de données sur un serveur qui prend en charge la sauvegarde ou utilisez une sauvegarde compatible avec ce serveur.|  
  
## <a name="explanation"></a>Explication  
Certaines fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affectent la structure des fichiers de base de données. Lorsque vous restaurez une base de données dans une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le format de fichier peut ne pas être compatible avec une autre version du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
Par exemple, cette erreur peut se produire si vous utilisez le format de stockage vardecimal dans une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis que vous essayez de restaurer les fichiers de base de données dans une version antérieure à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Identifiez la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécute sur le serveur d'origine. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur le serveur et cliquez sur **Propriétés**, ou tapez **SELECT @@VERSION** dans une fenêtre de requête. Ouvrez la base de données en utilisant la version d'origine de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Examinez les fonctionnalités qui sont activées sur la base de données d'origine dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Modifiez ces paramètres de façon à utiliser la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle la base de données sera restaurée.  
  
