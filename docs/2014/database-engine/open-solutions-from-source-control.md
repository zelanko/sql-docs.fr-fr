---
title: Ouvrir des solutions à partir du contrôle de code source | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b6d998956497eb0fb15f3b99de8e543636266e32
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930340"
---
# <a name="open-solutions-from-source-control"></a>Ouvrir des solutions à partir du contrôle de code source
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour ouvrir des solutions directement à partir du contrôle de code source. Lorsque vous effectuez cette opération, l'environnement Studio crée une copie de la toute dernière version des fichiers solutions à l'emplacement que vous avez spécifié.  
  
 Si aucune copie locale de la solution ne figure sur votre disque local, vous devez ouvrir le projet à partir du contrôle de code source avant de pouvoir utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour extraire la solution ou récupérer les fichiers solutions.  
  
> [!NOTE]  
>  Si vous disposez déjà d'une copie locale de la solution dont vous procédez à l'ouverture à partir du contrôle de code source, le système vous demande de remplacer la copie locale.  
  
### <a name="to-open-a-solution-from-source-control"></a>Pour ouvrir une solution à partir du contrôle de code source  
  
1.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **ouvrir à partir du contrôle de code source**.  
  
2.  Si le système vous le demande, connectez-vous à [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.  
  
3.  Dans la boîte de dialogue **créer un projet local à partir de SourceSafe** , sélectionnez le dossier qui contient la solution que vous souhaitez ouvrir, puis cliquez sur **OK**.  
  
4.  Si un dossier de travail de la solution existe déjà sur votre lecteur de disque local, la zone **créer un nouveau projet dans le dossier** change pour identifier le répertoire local. En l'absence de dossier de travail pour la solution en question, vous pouvez indiquer le dossier local dans lequel vous souhaitez ouvrir la solution ou encore naviguer jusqu'à lui.  
  
5.  Dans la boîte de dialogue **ouvrir une solution** , sélectionnez le fichier solution, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir des projets à partir du contrôle de code source](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
