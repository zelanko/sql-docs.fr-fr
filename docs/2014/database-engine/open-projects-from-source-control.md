---
title: Ouvrir des projets à partir du contrôle de code source | Microsoft Docs
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
ms.openlocfilehash: 4e8c391010cdcccce4631fff894e7cbd72001342
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930459"
---
# <a name="open-projects-from-source-control"></a>Ouvrir des projets à partir du contrôle de code source
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour ouvrir des projets directement à partir du contrôle de code source. Lorsque vous effectuez cette opération, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] récupère la dernière version du projet et la copie sur votre disque local. L'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] crée également automatiquement une solution pour le projet.  
  
 Une fois un projet ouvert à partir du contrôle de code source, vous pouvez extraire et modifier des fichiers projet.  
  
> [!NOTE]  
>  La procédure qui suit ne doit être utilisée qu'une seule fois. Ensuite, vous devez ouvrir le projet comme n’importe quel autre projet (en cliquant sur **fichier**, **ouvrir**, puis **projet**).  
  
### <a name="to-open-a-project-from-source-control"></a>Pour ouvrir un projet à partir du contrôle de code source  
  
1.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **ouvrir à partir du contrôle de code source**.  
  
2.  Si le système vous le demande, connectez-vous à [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  Dans la boîte de dialogue **créer un projet local à partir de SourceSafe** , ouvrez le dossier qui contient le projet à ouvrir.  
  
4.  La zone **créer un nouveau projet dans le dossier** change pour identifier le répertoire local dans lequel le projet sera créé. Si vous souhaitez placer le projet dans un autre répertoire, tapez le chemin d’accès au répertoire ou utilisez le bouton **Parcourir** pour localiser le répertoire sur votre disque local.  
  
5.  Dans la **zone créer un nouveau projet dans le dossier**, vérifiez que le dossier approprié est affiché, puis cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue **ouvrir une solution** , sélectionnez le projet que vous souhaitez ouvrir, puis cliquez sur **ouvrir**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir des solutions et des projets à partir du contrôle de code source](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)   
 [Ouvrir des solutions à partir du contrôle de code source](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
