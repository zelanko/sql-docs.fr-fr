---
title: Fichiers divers | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e939419a42231a7885a2d957bca218725e19ae80
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044885"
---
# <a name="miscellaneous-files"></a>Fichiers divers
  Les fichiers externes à un projet sont appelés *fichiers divers*. Lorsqu'une solution est ouverte, vous pouvez ouvrir et modifier les fichiers divers associés au projet. Un fichier est considéré comme un fichier divers si son extension n'est pas associée à l'éditeur de code du projet. Par exemple, dans les projets de script [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les fichiers dotés de l’extension .txt ou .mdx sont traités comme des fichiers divers. Dans un projet MDX, les fichiers dotés de l'extension .txt ou .sql sont également traités comme des fichiers divers. Pour associer une extension de fichier avec un éditeur de code, consultez [associer des Extensions de fichier à un éditeur de Code](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
 Il est utile de pouvoir ajouter des fichiers divers à un projet pour plusieurs raisons. Vous pouvez avoir un fichier qui n'est pas nécessairement un script reconnu mais qui est indispensable au développement de la solution, tel que des instructions ou conseils de développement, des fichiers de données ou des clips de code.  
  
 Les fichiers divers offrent une certaine souplesse. Supposons, par exemple, que votre projet de script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient plusieurs scripts pour la création de tables et de procédures stockées dans votre base de données. Vous disposez également de plusieurs fichiers de données pour les tables (dotés de l'extension de fichier .BCP) et d'instructions d'exécution dans un fichier LISEZMOI. Vous pouvez alors attacher les fichiers de données et le fichier LISEZMOI en tant que fichiers divers au projet pour tirer parti du contrôle de code source et d'autres fonctionnalités du système de projet.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Les menus et les barres d’outils changent selon le format du fichier que vous ouvrez. Lorsque vous ouvrez un fichier texte, par exemple, la barre d'outils Éditeur de texte s'affiche. Si vous ouvrez un schéma XML, la barre d'outils correspondante s'affiche. Lorsque vous modifiez le schéma XML, la barre d'outils Éditeur de texte n'est pas disponible. Lorsque vous passez d'un fichier de projet à un fichier divers, toutes les commandes et les barres d'outils associées au projet disparaissent et seules celles directement associées au fichier divers s'affichent.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de gestion de Solutions et projets](files-that-manage-solutions-and-projects.md)   
 [Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Projets &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md)  
  
  