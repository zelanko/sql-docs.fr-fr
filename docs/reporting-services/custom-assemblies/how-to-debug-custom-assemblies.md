---
title: "Comment : déboguer des assemblys personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
caps.latest.revision: 44
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b6cdc41f90765a3fc1a568bc76ddf0d41c15b38a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="how-to-debug-custom-assemblies"></a>Procédure : déboguer des assemblys personnalisés
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit plusieurs outils de débogage qui peuvent vous aider à analyser votre code de l’assembly personnalisé et localiser les erreurs qu’il contient. Vous devez choisir un outil en fonction de ce que vous essayez d'accomplir. Cet exemple utilise [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].  
  
 La méthode recommandée pour concevoir, développer et tester des assemblys personnalisés pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste à créer une solution contenant à la fois vos rapports de test et votre assembly personnalisé.  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>Pour déboguer des assemblys à l'aide d'une instance unique de Visual Studio  
  
1.  Créez un projet de rapport à l'aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
     En même temps que vous créez un projet de rapport, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] crée une solution destinée à le contenir.  
  
2.  Ajoutez un nouveau projet Bibliothèque de classes à la solution existante. Assurez-vous que le projet de rapport est défini comme projet de démarrage. Pour plus d'informations sur la procédure à suivre, consultez la documentation de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
3.  Dans l'Explorateur de solutions, sélectionnez la solution de votre choix.  
  
4.  Sur le **vue** menu, cliquez sur **Pages de propriétés**.  
  
     Le **les Pages de propriétés de Solution** boîte de dialogue s’ouvre.  
  
5.  Dans le volet gauche, développez **propriétés communes** si nécessaire, puis cliquez sur **dépendances du projet**. Sélectionnez le projet de rapport à partir de la **projet** liste déroulante. Sélectionnez votre projet d’assembly dans le **dépend** liste.  
  
6.  Cliquez sur **OK** pour enregistrer les modifications et fermer la **Pages de propriétés** boîte de dialogue.  
  
7.  Dans l'Explorateur de solutions, sélectionnez votre projet d'assembly personnalisé.  
  
8.  Sur le **vue** menu, cliquez sur **Pages de propriétés**.  
  
     Le **les Pages de propriétés de projet** boîte de dialogue s’ouvre.  
  
9. Cliquez sur le **générer** onglet si vous êtes dans un projet c# ou le **compiler** si vous êtes dans l’onglet un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projet.  
  
10. Sur le **générer**/**compiler** , entrez le chemin d’accès au dossier Concepteur de rapports. Par défaut, il s’agit de C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) dans le **chemin de sortie** zone de texte. Une version mise à jour de votre assembly personnalisé est alors générée et déployée directement dans le Concepteur de rapports avant exécution de votre rapport.  
  
11. Une fois votre rapport généré et votre assembly personnalisé développé, définissez des points d'arrêt dans le code de votre assembly personnalisé.  
  
12. Exécutez le rapport sous **DebugLocal** mode en appuyant sur la touche F5. Lorsque le rapport s'exécute dans la fenêtre d'aperçu contextuelle, le débogueur atteint chacun des points d'arrêt correspondant au code exécutable de votre assembly. Utilisez la touche F11 pour exécuter le code de votre assembly personnalisé en pas à pas.  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>Pour déboguer des assemblys à l'aide de deux instances de Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et ouvrez votre projet d'assembly personnalisé.  
  
2.  Générez le projet et déployez votre assembly personnalisé de même que le fichier .pdb associé dans le Concepteur de rapports. Pour plus d’informations sur le déploiement, consultez [déploiement d’un Assembly personnalisé](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md).  
  
3.  Ouvrez un projet de rapport utilisant votre assembly personnalisé en laissant votre code d'assembly personnalisé ouvert dans une instance distincte de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
4.  Naviguez vers l'instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qui contient votre projet d'assembly personnalisé et définissez des points d'arrêt dans votre code.  
  
5.  Le projet d’assembly personnalisé demeurant dans la fenêtre active, cliquez sur **attacher au processus** sur la **déboguer** menu.  
  
     Le **attacher au processus** boîte de dialogue s’ouvre.  
  
6.  Dans la liste de processus, sélectionnez le processus devenv.exe qui correspond à votre projet de rapport et cliquez sur **attacher**.  
  
7.  Définissez les expressions qui vous utiliserez dans votre rapport à partir de votre assembly personnalisé et concevez votre rapport.  
  
8.  Lorsque vous avez terminé la conception de votre rapport, cliquez sur le **aperçu** onglet.  
  
     Le rapport s'exécute et le code de l'assembly personnalisé doit s'arrêter aux points d'arrêt prédéfinis.  
  
    > [!NOTE]  
    >  À l’aide de la **aperçu** onglet n’applique pas les autorisations de code de l’assembly. Pour un test complet, qui inclut toutes les erreurs de sécurité de l’accès de code, démarrez le projet de rapport sous la **DebugLocal** paramètre de configuration.  
  
9. Exécutez le code pas à pas à l'aide de la touche F11. Pour plus d'informations sur le débogage à l'aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], consultez la documentation de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
