---
title: Partager des fichiers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9e779a0c0da9920b2efda5f52135e85f31959d10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224709"
---
# <a name="share-files"></a>Partager des fichiers
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour partager des éléments avec des projets du contrôle de code source. Lorsque vous partagez un élément, toute modification apportée à cet élément est réfléchie sur chaque projet avec lequel l'élément est partagé.  
  
 Le partage d'éléments présente les avantages suivants aux utilisateurs du contrôle de code source :  
  
-   Chaque projet qui utilise un élément partagé n'est pas tenu de stocker une copie distincte de cet élément, ce qui permet d'économiser de l'espace disque à la fois sur le serveur et sur le client du contrôle de code source. Le fournisseur de contrôle de code source stocke l'élément partagé à un emplacement centralisé et chaque projet avec lequel il est partagé stocke un pointeur désignant cet emplacement.  
  
-   Les risques d'incompatibilité entre les versions sont écartés. Comme chaque projet avec lequel l'élément est partagé utilise la même version de cet élément, tout conflit survenant lors de la modification indépendante de chaque copie d'un élément dans plusieurs projets est évité.  
  
### <a name="to-share-an-item"></a>Pour partager un élément  
  
1.  Dans l'Explorateur de solutions, sélectionnez le dossier ou le projet dans lequel vous souhaitez placer les fichiers partagés.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **partage**.  
  
3.  Dans le **partager avec** boîte de dialogue Parcourir la liste de répertoires pour l’élément que vous souhaitez partager, puis cliquez sur cet élément.  
  
4.  Cliquez sur **partage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du contrôle de code source](../../2014/database-engine/source-control-basics.md)  
  
  
