---
title: Démarrer SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94466dc6c069ced5b2743cbd8a14d98271303477
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188843"
---
# <a name="start-sql-server-management-studio"></a>Démarrer SQL Server Management Studio
  Pour commencer ce didacticiel, commençons par regarder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Ouverture de SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>Pour ouvrir SQL Server Management Studio  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], puis cliquez sur **SQL Server Management Studio**.  
  
    > [!NOTE]  
    >  Par défaut, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] n'est pas installé. Si [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] n'est pas disponible, installez-le en exécutant le programme d'installation. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] n’est pas disponible avec [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express est disponible en téléchargement gratuit à partir de la [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=37075&clcid=0x409), mais a une interface utilisateur différente qu’est décrite dans ce didacticiel.  
  
2.  Dans la boîte de dialogue **Se connecter à un serveur** , vérifiez les paramètres par défaut, puis cliquez sur **Se connecter**. Pour vous connecter, le **nom du serveur** zone doit contenir le nom de l’ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé. Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est une instance nommée, le **nom du serveur** zone doit également contenir le nom d’instance dans le format \< *Nom_Ordinateur* > \\ < *nom_instance*>.  
  
## <a name="management-studio-components"></a>Composants Management Studio  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] fournit des informations dans des fenêtres dédiées à des types d’informations précis. Les informations sur les bases de données s'affichent dans l'Explorateur d'objets et dans des fenêtres de documents.  
  
-   L'Explorateur d'objets est une arborescence qui présente tous les objets de base de données sur un serveur. Cela peut inclure les bases de données du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'Explorateur d'objets contient des informations sur tous les serveurs auxquels il est connecté. Lorsque vous ouvrez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], le système vous demande de vous connecter à l'Explorateur d'objets avec les derniers paramètres utilisés. Vous pouvez double-cliquer sur n'importe quel serveur dans la fenêtre Serveurs inscrits pour y établir une connexion, mais il n'est pas nécessaire d'inscrire un serveur pour pouvoir vous y connecter.  
  
-   La fenêtre de document occupe la plus grande partie de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Elle contient les fenêtres des éditeurs de requêtes et du navigateur. Par défaut, la page Résumé s’affiche, connectée à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur l’ordinateur actif.  
  
## <a name="showing-additional-windows"></a>Affichage de fenêtres supplémentaires  
  
#### <a name="to-show-the-registered-servers-window"></a>Pour afficher la fenêtre Serveurs inscrits  
  
1.  Dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
     La fenêtre Serveurs inscrits apparaît au-dessus de l'Explorateur d'objets. La fenêtre Serveurs inscrits présente la liste des serveurs que vous administrez fréquemment. Il est possible d'ajouter et de supprimer des serveurs de cette liste. Les seuls serveurs répertoriés sont les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur sur lequel vous exécutez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Si votre serveur n’apparaît pas, dans serveurs inscrits, cliquez sur **moteur de base de données**, puis cliquez sur **l’inscription du serveur Local mise à jour**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Connexion avec le composant Serveurs inscrits et l'Explorateur d'objets](../object/object-explorer.md)  
  
  
