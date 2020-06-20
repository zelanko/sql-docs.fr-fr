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
ms.openlocfilehash: 79909fcdb09e349798edfe285475f8a898c3bf04
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84929020"
---
# <a name="share-files"></a>Partager des fichiers
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour partager des éléments avec des projets du contrôle de code source. Lorsque vous partagez un élément, toute modification apportée à cet élément est réfléchie sur chaque projet avec lequel l'élément est partagé.  
  
 Le partage d'éléments présente les avantages suivants aux utilisateurs du contrôle de code source :  
  
-   Chaque projet qui utilise un élément partagé n'est pas tenu de stocker une copie distincte de cet élément, ce qui permet d'économiser de l'espace disque à la fois sur le serveur et sur le client du contrôle de code source. Le fournisseur de contrôle de code source stocke l'élément partagé à un emplacement centralisé et chaque projet avec lequel il est partagé stocke un pointeur désignant cet emplacement.  
  
-   Les risques d'incompatibilité entre les versions sont écartés. Comme chaque projet avec lequel l'élément est partagé utilise la même version de cet élément, tout conflit survenant lors de la modification indépendante de chaque copie d'un élément dans plusieurs projets est évité.  
  
### <a name="to-share-an-item"></a>Pour partager un élément  
  
1.  Dans l'Explorateur de solutions, sélectionnez le dossier ou le projet dans lequel vous souhaitez placer les fichiers partagés.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **partager**.  
  
3.  Dans la boîte de dialogue **partager avec** , recherchez dans la liste des répertoires l’élément que vous souhaitez partager, puis cliquez sur cet élément.  
  
4.  Cliquez sur **Partager**.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du contrôle de code source](../../2014/database-engine/source-control-basics.md)  
  
  
