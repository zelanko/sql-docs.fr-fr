---
title: "Se connecter avec le composant Serveurs inscrits et l’Explorateur d’objets | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: f5dc51dc1a49d66d6ea5194cb3357ecea6fb876f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-1-2---connect-with-registered-servers-and-object-explorer"></a>Leçon 1-2 - Se connecter avec le composant Serveurs inscrits et l’Explorateur d’objets
Ce didacticiel montre l'utilisation des serveurs inscrits et de l'Explorateur d'objets.  
  
Ce didacticiel utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Pour optimiser la sécurité, les exemples de bases de données ne sont pas installés par défaut. Pour plus d’informations, consultez [Installation d’exemples et d’exemples de bases de données SQL Server](http://sqlserversamples.codeplex.com).  
  
## <a name="connecting-to-servers"></a>Connexion à des serveurs  
La barre d'outils du composant Serveurs inscrits comprend des boutons pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Vous pouvez inscrire un ou plusieurs de ces types de serveurs pour une administration plus aisée. Effectuez l'exercice ci-après pour inscrire la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
#### <a name="to-register-the-database"></a>Pour enregistrer la base de données  
  
1.  Dans la barre d’outils Serveurs inscrits, cliquez sur **Moteur de base de données** si nécessaire. (Il se peut qu'il soit déjà sélectionné.)  
  
2.  Développez **Moteur de base de données**.  
  
3.  Cliquez avec le bouton droit sur **Groupes de serveurs locaux**, puis cliquez sur **Nouvelle inscription de serveur**.  
  
4.  Dans la boîte de dialogue **Nouvelle inscription de serveur** , dans la zone de texte **Nom du serveur** , tapez le nom de votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Dans la zone **Nom du serveur inscrit** , tapez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
6.  Sous l’onglet **Propriétés de connexion**, dans la liste **Se connecter à la base de données**, sélectionnez **\<Parcourir le serveur…>**.  
  
7.  Dans la boîte de dialogue **Rechercher les bases de données** , cliquez sur **Oui**.  
  
8.  Dans la boîte de dialogue **Rechercher une base de données sur le serveur** , sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis cliquez sur **OK**.  
  
9. Cliquez sur **Tester**pour vérifier que le serveur a été inscrit correctement.  
  
10. Dans la boîte de dialogue **Nouvelle inscription de serveur** , cliquez sur **Enregistrer**.  
  
## <a name="connecting-with-object-explorer"></a>Connexion avec l'Explorateur d'objets  
Tout comme le composant Serveurs inscrits, l'Explorateur d'objets peut se connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]et à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
#### <a name="to-connect-with-object-explorer"></a>Pour se connecter avec l'Explorateur d'objets  
  
1.  Dans la barre d’outils de l’Explorateur d’objets, cliquez sur **Se connecter** pour dérouler la liste des types de connexions possibles, puis sélectionnez **Moteur de base de données**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , dans la zone de texte **Nom du serveur** , tapez le nom de votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Cliquez sur **Options** et parcourez la liste des choix.  
  
4.  Cliquez sur **Se connecter**pour vous connecter au serveur. Si vous étiez déjà connecté, l'Explorateur d'objets s'affiche de nouveau et ce serveur est activé.  
  
    Avec l'Explorateur d'objets, vous pouvez administrer la sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la réplication et la messagerie de base de données. L'Explorateur d'objets peut gérer uniquement certaines fonctionnalités de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Chacun de ces composants disposent d'outils spécialisés supplémentaires.  
  
5.  Dans l’Explorateur d’objets, développez le dossier **Bases de données** et sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    Notez que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] présente les bases de données système dans un dossier séparé.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Modifier la disposition d'environnement](../../tools/sql-server-management-studio/lesson-1-3-change-the-environment-layout.md)  
  
  
  

