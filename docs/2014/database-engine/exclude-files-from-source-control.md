---
title: Exclure des fichiers de contrôle de code Source | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 42ae16970e59e2eac1af68e54a38b19bd760c068
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62779899"
---
# <a name="exclude-files-from-source-control"></a>Exclure des fichiers du contrôle de code source
  Si la solution que vous travaillez sur contient des fichiers qui ne nécessitent pas de services de contrôle de code source, vous pouvez utiliser la **exclure du contrôle de Source** commande pour exclure le fichier de contrôle de code source. Lorsque vous effectuez cette opération, le fichier reste dans la base de données de [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, mais il ne fait plus l'objet d'archivage ni d'extraction dans le cadre du projet.  
  
 Vous devez utiliser le **exclure du contrôle de Source** commande uniquement sur les fichiers générés. Un fichier généré est un qui peut être intégralement recréé par [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en fonction du contenu d’un autre fichier dans la solution.  
  
### <a name="to-exclude-a-file-from-source-control"></a>Pour exclure un fichier du contrôle de code source  
  
1.  Dans l'Explorateur de solutions, sélectionnez le fichier à exclure.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **exclure**  *\<nom de fichier >* **à partir de Contrôle de code source**.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de contrôle de code source](../../2014/database-engine/source-control-basics.md)   
 [Définir les Options de contrôle de code Source](../../2014/database-engine/set-source-control-options.md)   
 [Modifier les connexions du contrôle de code source](../../2014/database-engine/change-source-control-connections.md)  
  
  
