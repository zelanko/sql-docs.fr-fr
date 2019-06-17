---
title: Ouvrir des projets à partir du contrôle de code Source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec14f86b283fa8ccbc037feec4a8a54983126403
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62774953"
---
# <a name="open-projects-from-source-control"></a>Ouvrir des projets à partir du contrôle de code source
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour ouvrir des projets directement à partir du contrôle de code source. Lorsque vous effectuez cette opération, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] récupère la dernière version du projet et la copie sur votre disque local. L'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] crée également automatiquement une solution pour le projet.  
  
 Une fois un projet ouvert à partir du contrôle de code source, vous pouvez extraire et modifier des fichiers projet.  
  
> [!NOTE]  
>  La procédure qui suit ne doit être utilisée qu'une seule fois. Par la suite, vous devez ouvrir le projet comme n’importe quel autre projet (en cliquant sur **fichier**, **ouvrir**, puis **projet**).  
  
### <a name="to-open-a-project-from-source-control"></a>Pour ouvrir un projet à partir du contrôle de code source  
  
1.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **ouvert à partir d’un contrôle de code Source**.  
  
2.  Si le système vous le demande, connectez-vous à [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  Dans le **créer un projet local à partir de SourceSafe** boîte de dialogue zone, ouvrez le dossier qui contient le projet à ouvrir.  
  
4.  Le **créer un nouveau projet dans le dossier** zone change et indique le répertoire local dans lequel le projet sera créé. Si vous souhaitez placer le projet dans un autre répertoire, tapez le chemin d’accès au répertoire ou utilisez le **Parcourir** pour localiser le répertoire sur votre disque local.  
  
5.  Dans le **créer un nouveau projet dans la zone dossier**, vérifiez que le dossier approprié s’affiche, puis cliquez sur **OK**.  
  
6.  Dans le **ouvrir une Solution** boîte de dialogue, sélectionnez le projet que vous souhaitez ouvrir, puis cliquez sur **ouvrir**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir des Solutions et projets de contrôle de code Source](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)   
 [Ouvrir des solutions à partir du contrôle de code source](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
