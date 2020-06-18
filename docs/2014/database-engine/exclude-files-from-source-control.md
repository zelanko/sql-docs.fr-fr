---
title: Exclure des fichiers du contrôle de code source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933087"
---
# <a name="exclude-files-from-source-control"></a>Exclure des fichiers du contrôle de code source
  Si la solution sur laquelle vous travaillez contient des fichiers qui ne nécessitent pas de services de contrôle de code source, vous pouvez utiliser la commande **exclure du contrôle de code source** pour exclure le fichier du contrôle de code source. Lorsque vous effectuez cette opération, le fichier reste dans la base de données de [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, mais il ne fait plus l'objet d'archivage ni d'extraction dans le cadre du projet.  
  
 Vous devez utiliser la commande **exclure du contrôle de code source** uniquement sur les fichiers générés. Un fichier généré est un fichier qui peut être entièrement recréé par en [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] fonction du contenu d’un autre fichier dans la solution.  
  
### <a name="to-exclude-a-file-from-source-control"></a>Pour exclure un fichier du contrôle de code source  
  
1.  Dans l'Explorateur de solutions, sélectionnez le fichier à exclure.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **exclure** *\<file name>* **du contrôle de code source**.  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base sur le contrôle de code source](../../2014/database-engine/source-control-basics.md)   
 [Définir les options de contrôle de code source](../../2014/database-engine/set-source-control-options.md)   
 [Modifier les connexions du contrôle de code source](../../2014/database-engine/change-source-control-connections.md)  
  
  
