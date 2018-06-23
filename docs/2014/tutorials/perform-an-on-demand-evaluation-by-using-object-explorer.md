---
title: Effectuer une évaluation à la demande à l’aide de l’Explorateur d’objets | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 55ca364c60c2b9fcca407561ed195035ce7205fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044867"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>Effectuer une évaluation à la demande à l'aide de l'Explorateur d'objets
  Dans cette tâche, vous allez utiliser l’Explorateur d’objets pour effectuer une évaluation à la demande des stratégies des meilleures pratiques pour la [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] sur une instance unique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Vous pouvez également évaluer des stratégies sur une instance unique via des serveurs inscrits. Pour plus d’informations, consultez [effectuer une évaluation à la demande par les serveurs inscrits à l’aide de](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Cette leçon est basée sur la version de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Pour effectuer une évaluation à la demande des stratégies des meilleures pratiques par rapport aux instances qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], vous devez utiliser la procédure dans la rubrique [effectuer une évaluation à la demande par les serveurs inscrits à l’aide de](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>Pour effectuer une évaluation à la demande à l'aide de l'Explorateur d'objets  
  
1.  Démarrer [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], puis connectez-vous à le [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  Dans l’Explorateur d’objets, développez **gestion**, développez **gestion des stratégies de**, avec le bouton droit **stratégies**, puis cliquez sur **évaluer**.  
  
    > [!NOTE]  
    >  Par défaut, l'instance locale est utilisée comme source des stratégies. Si vous avez précédemment importé des stratégies des meilleures pratiques, elles apparaîtront avec toutes les autres stratégies que vous avez créées. Vous pouvez sélectionner l’un des stratégies des meilleures pratiques importées, puis cliquez sur **évaluer**. Si vous n'avez pas importé les stratégies des meilleures pratiques, continuez cette procédure.  
  
3.  Dans le **évaluer les stratégies** boîte de dialogue, à côté du **Source** , cliquez sur le bouton de sélection (**...** ) bouton.  
  
4.  Dans le **sélectionner une Source** boîte de dialogue, vous pouvez sélectionner **fichiers** ou **Server** comme source des fichiers de stratégie à évaluer. Si vous cliquez sur **Server**, vous pouvez effectuer une évaluation de la demande de toutes les stratégies des meilleures pratiques qui ont été précédemment importées dans la gestion basée sur un serveur local ou distant. Dans ce didacticiel, vous cliquerez sur **fichiers**, puis sélectionnez les fichiers de stratégie individuels que vous souhaitez évaluer. Pour cela, procédez comme suit :  
  
    1.  Cliquez sur **fichiers**.  
  
    2.  Regard **fichiers**, cliquez sur le bouton de sélection (**...** ) bouton.  
  
    3.  Dans le **sélectionner la stratégie** boîte de dialogue, accédez au dossier suivant, qui contient les stratégies des meilleures pratiques :  
  
         **C:\Program fichiers (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  Le chemin d'accès du fichier varie, selon l'emplacement d'installation des fichiers programme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], si vous exécutez un système d'exploitation 32 bits ou 64 bits, et selon l'identificateur de langue.  
  
    4.  Sélectionnez un ou plusieurs fichiers de stratégie .xml à évaluer, puis cliquez sur **ouvrir**.  
  
         La liste des fichiers sélectionnés s’affiche dans le **fichiers** boîte.  
  
    5.  Dans le **sélectionner une Source** boîte de dialogue, cliquez sur **OK**.  
  
    6.  Si le **chargement de stratégies** boîte de dialogue s’affiche, cliquez sur **fermer**.  
  
     Les stratégies que vous avez sélectionnés sont répertoriés dans le **sélection de la stratégie** page. Gardez à l'esprit qu'une icône d'avertissement en regard d'une stratégie indique que la stratégie contient des scripts.  
  
5.  Cliquez sur **évaluer** pour évaluer les stratégies.  
  
     Dans le **résultats** de table, les résultats pour chaque stratégie sont répertoriées. Une icône rouge avec un x indique que la conformité aux stratégies a échoué.  
  
6.  Pour certains échecs de stratégie, la Gestion basée sur des stratégies vous permet de mettre immédiatement en vigueur la conformité aux stratégies sur la cible. Pour de tels échecs, une case à cocher s'affichera en regard de la stratégie qui a échoué. Si vous sélectionnez la case à cocher, le **appliquer** bouton devient disponible. Lorsque vous cliquez sur **appliquer**, le paramètre non conforme sera être automatiquement mis à jour sur l’instance cible.  
  
    > [!CAUTION]  
    >  Assurez-vous de bien comprendre le paramètre de stratégie avant de mettre à jour automatiquement une instance cible. Nous vous recommandons d’après avoir sélectionné une ou plusieurs cases à cocher, **Script**, choisissez un emplacement de sortie afin que vous puissiez examiner sous-jacent [!INCLUDE[tsql](../includes/tsql-md.md)] avant d’appliquer les modifications de code.  
  
7.  Pour afficher les résultats détaillés pour une stratégie, cliquez sur la stratégie dans le **résultats** table.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Effectuer une évaluation à la demande à l’aide de serveurs inscrits](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  