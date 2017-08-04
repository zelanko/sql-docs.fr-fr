---
title: "Génération, déploiement et débogage des objets personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99fdd71403b12cee8ba9f207890268cde2e1d450
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="building-deploying-and-debugging-custom-objects"></a>Génération, déploiement et débogage d'objets personnalisés
  Une fois que vous avez écrit le code pour un objet personnalisé pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez générer l’assembly, déployer et intégrer dans [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur pour le rendre disponible pour une utilisation dans des packages et la tester et la déboguer.  
  
##  <a name="top"></a>Étapes de génération, déploiement et débogage d’un objet personnalisé pour Integration Services  
 Vous avez déjà écrit les fonctionnalités personnalisées de votre objet. À présent, vous devez les tester et les rendre disponibles aux utilisateurs. Les étapes sont très similaires pour tous les types d'objets personnalisés que vous pouvez créer pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Voici les étapes pour générer, déployer et tester.  
  
1.  [Signe](#signing) l’assembly doit être créé avec un nom fort.  
  
2.  [Build](#building) l’assembly.  
  
3.  [Déployer](#deploying) l’assembly en déplaçant ou en copiant approprié [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dossier.  
  
4.  [Installer](#installing) l’assembly dans le global assembly cache (GAC).  
  
     L'objet est automatiquement ajouté à la boîte à outils.  
  
5.  [Résoudre les problèmes](#troubleshooting) le déploiement, si nécessaire.  
  
6.  [Test](#testing) et déboguer votre code.  
  
 Vous pouvez maintenant utiliser le concepteur SSIS dans SQL Server Data Tools (SSDT) pour créer, gérer et exécuter des packages qui ciblent des versions différentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur l’impact de cette amélioration sur vos extensions personnalisées, consultez [mise en route de vos extensions personnalisées de SSIS pour être pris en charge par la prise en charge de plusieurs version de SSDT 2015 pour SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/)  
  
##  <a name="signing"></a>Signature de l’Assembly  
 Lorsqu'un assembly est destiné à être partagé, il doit être installé dans le Global Assembly Cache. Une fois que l'assembly est ajouté au Global Assembly Cache, il peut être utilisé par des applications telles que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Une exigence du Global Assembly Cache stipule que l'assembly doit être signé avec un nom fort, lequel garantit qu'un assembly est globalement unique. Un assembly avec nom fort possède un nom qualifié complet qui comprend son nom, sa culture, sa clé publique et son numéro de version. Le runtime utilise ces informations pour rechercher l'assembly et le distinguer des autres assemblys portant le même nom.  
  
 Pour signer un assembly avec un nom fort, vous devez d'abord avoir ou créer une paire de clés publique/privée. Cette paire de clés de chiffrement publique et privée est utilisée au moment de la génération pour créer un assembly avec nom fort.  
  
 Pour plus d'informations sur les noms forts et sur les étapes à suivre pour signer un assembly, consultez les rubriques suivantes dans la documentation du Kit de développement logiciel [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] :  
  
-   Assemblys avec noms forts  
  
-   Création d'une paire de clés  
  
-   Signature d'un assembly avec un nom fort  
  
 Vous pouvez signer facilement votre assembly avec un nom fort dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] au moment de la génération. Dans le **propriétés du projet** boîte de dialogue, sélectionnez le **signature** onglet. Sélectionnez l’option de **signer l’assembly** , puis indiquez le chemin d’accès du fichier de clé (.snk).  
  
##  <a name="building"></a>Génération de l’Assembly  
 Après avoir signé le projet, vous devez générer ou régénérer le projet ou la solution en utilisant les commandes disponibles sur le **générer** menu de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Votre solution peut contenir un projet séparé d' interface utilisateur personnalisée, lequel doit également être signé avec un nom fort et peut être généré en même temps.  
  
 La méthode la plus pratique pour effectuer les deux étapes suivantes, à savoir le déploiement de l'assembly et son installation dans le Global Assembly Cache, consiste à écrire le script de ces étapes sous la forme d'un événement post-build dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Événements de build sont disponibles à partir de la **compiler** page de propriétés du projet pour un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projet et à partir de la **des événements de Build** page pour un projet c#. Le chemin d’accès complet est requis pour les utilitaires d’invite de commandes comme **gacutil.exe**. Les guillemets sont requis à la fois autour des chemins d'accès qui contiennent des espaces et autour des macros telles que $(TargetPath) qui s'étendent aux chemins d'accès qui contiennent des espaces.  
  
 Voici un exemple de ligne de commande d'événement après génération pour un module fournisseur d'informations personnalisé :  
  
```  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)  
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\130\DTS\LogProviders "  
```  
  
##  <a name="deploying"></a>Déploiement de l’Assembly  
 Le [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur localise les objets personnalisés disponibles pour une utilisation dans des packages en énumérant les fichiers figurant dans une série de dossiers qui sont créés lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est installé. Lorsque la valeur par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les paramètres d’installation sont utilisés, cet ensemble de dossiers se trouve sous **C:\Program Files\Microsoft SQL Server\130\DTS**. Toutefois si vous créez un programme d’installation pour votre objet personnalisé, vous devez vérifier la valeur de la **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\SSIS\Setup\DtsPath** clé de Registre pour vérifier l’emplacement de ce dossier.  
  
> [!NOTE]  
>  Pour plus d’informations sur le déploiement des composants personnalisés pour fonctionner avec la prise en charge de plusieurs version de SQL Server Data Tools, consultez [mise en route de vos extensions personnalisées de SSIS pour être pris en charge par la prise en charge de plusieurs version de SSDT 2015 pour SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/).  
  
 Vous pouvez placer l'assembly dans le dossier de deux manières :  
  
-   Déplacez ou copiez l'assembly compilé vers le dossier approprié après l'avoir généré. (Par commodité, vous pouvez inclure la commande de copie dans un événement après génération.)  
  
-   Générez directement l'assembly dans le dossier approprié.  
  
 Les dossiers de déploiement suivants sous **C:\Program Files\Microsoft SQL Server\130\DTS** sont utilisés pour les différents types d’objets personnalisés :  
  
|Objet personnalisé|Dossier de déploiement|  
|-------------------|-----------------------|  
|Tâche|Tâches|  
|Gestionnaire de connexions|Connexions|  
|Module fournisseur d'informations|LogProviders|  
|Composant de flux de données|PipelineComponents|  
  
> [!NOTE]  
>  Les assemblys sont copiés vers ces dossiers pour prendre en charge l'énumération des tâches, gestionnaires de connexions, etc. disponibles. Par conséquent, vous ne devez pas déployer des assemblys qui contiennent uniquement l'interface utilisateur personnalisée des objets personnalisés vers ces dossiers.  
  
##  <a name="installing"></a>Installation de l’Assembly dans le Global Assembly Cache  
 Pour installer l’assembly de tâche dans le global assembly cache (GAC), utilisez l’outil de ligne de commande **gacutil.exe**, ou faites glisser les assemblys à la `%system%\assembly` active. Pour plus de commodité, vous pouvez également inclure l’appel à **gacutil.exe** dans un événement post-build.  
  
 La commande suivante installe un composant nommé *MyTask.dll* dans le GAC à l’aide de **gacutil.exe**.  
  
 `gacutil /iF MyTask.dll`  
  
 Vous devez fermer et rouvrir le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] après avoir installé une nouvelle version de votre objet personnalisé. Si vous avez installé des versions antérieures de votre objet personnalisé dans le Global Assembly Cache, vous devez les supprimer avant d'installer la nouvelle version. Pour désinstaller un assembly, exécutez **gacutil.exe** et spécifiez le nom de l’assembly avec la `/u` option.  
  
 Pour plus d'informations sur le Global Assembly Cache, consultez Global Assembly Cache Tool (Gactutil.exe) dans [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Tools.  
  
##  <a name="troubleshooting"></a>Dépannage du déploiement  
 Si votre objet personnalisé s’affiche dans le **boîte à outils** ou la liste des objets disponibles, mais vous ne parvenez pas à ajouter à un package, essayez les opérations suivantes :  
  
1.  Recherchez plusieurs versions de votre composant dans le Global Assembly Cache. S'il existe plusieurs versions du composant dans le Global Assembly Cache, il est possible que le concepteur ne soit pas en mesure de charger votre composant. Supprimez toutes les instances de l'assembly dans le Global Assembly Cache et ajoutez de nouveau l'assembly.  
  
2.  Assurez-vous qu'une seule instance unique de l'assembly existe dans le dossier de déploiement.  
  
3.  Actualisez la boîte à outils.  
  
4.  Attacher [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à **devenv.exe** et définissez un point d’arrêt pour parcourir votre code d’initialisation pour vous assurer qu’aucune exception ne se produit.  
  
##  <a name="testing"></a>Tester et déboguer votre Code  
 L’approche la plus simple pour déboguer les méthodes d’exécution d’un objet personnalisé consiste à démarrer **dtexec.exe** de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] après avoir généré votre objet personnalisé et exécuter un package qui utilise le composant.  
  
 Si vous souhaitez déboguer les méthodes du composant au moment du design, comme le **Validate** (méthode), ouvrez un package qui utilise le composant dans une deuxième instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]et l’attacher à son **devenv.exe** processus.  
  
 Si vous souhaitez également déboguer les méthodes d’exécution du composant lorsqu’un package est ouvert et en cours d’exécution [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur, vous devez forcer une pause dans l’exécution du package afin que vous pouvez également attacher à la **DtsDebugHost.exe** processus.  
  
#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a>Pour déboguer les méthodes d'exécution d'un objet à l'aide d'un attachement à dtexec.exe  
  
1.  Signez et générez votre projet dans la configuration de débogage, déployez-le et installez-le dans le Global Assembly Cache comme indiqué dans cette rubrique.  
  
2.  Sur le **déboguer** onglet de **propriétés du projet**, sélectionnez **démarrer le programme externe** en tant que le **Action de démarrage**, recherchez **dtexec.exe**, qui est installé par défaut dans C:\Program Files\Microsoft SQL Server\130\DTS\Binn.  
  
3.  Dans le **les options de ligne de commande** zone de texte, sous **Options de démarrage**, entrez les arguments de ligne de commande requis pour exécuter un package qui utilise votre composant. Souvent, l'argument de ligne de commande sera consitué du commutateur /F[ILE] suivi du chemin d'accès et du nom du fichier .dtsx. Pour plus d'informations, consultez [dtexec Utility](../../integration-services/packages/dtexec-utility.md).  
  
4.  Définissez des points d'arrêt dans le code source aux emplacements appropriés dans les méthodes d'exécution de votre composant.  
  
5.  Exécutez votre projet.  
  
#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a>Pour déboguer les méthodes de conception d'un objet personnalisé via un attachement aux outils de données SQL Server  
  
1.  Signez et générez votre projet dans la configuration de débogage, déployez-le et installez-le dans le Global Assembly Cache comme indiqué dans cette rubrique.  
  
2.  Définissez des points d'arrêt dans le code source aux emplacements appropriés dans les méthodes de conception de votre objet personnalisé.  
  
3.  Ouvrez une deuxième instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et chargez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient un package qui utilise l'objet personnalisé.  
  
4.  À partir de la première instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], attacher à la deuxième instance de **devenv.exe** dans lequel le package est chargé en sélectionnant **attacher au processus** à partir de la **déboguer** menu de la première instance.  
  
5.  Exécutez le package à partir de la deuxième instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a>Pour déboguer les méthodes d'exécution d'un objet personnalisé via un attachement aux outils de données SQL Server  
  
1.  Une fois que vous avez effectué les étapes répertoriées dans la procédure précédente, forcez une pause dans l’exécution de votre package afin que vous pouvez attacher à **DtsDebugHost.exe**. Vous pouvez forcer cette pause en ajoutant un point d’arrêt à la **OnPreExecute** événement, ou en ajoutant une tâche de Script à votre projet et en entrant un script qui affiche une boîte de dialogue modale.  
  
2.  Exécutez le package. Lors de la pause se produit, basculez vers l’instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dans lequel votre projet de code est ouvert et sélectionnez **attacher au processus** à partir de la **déboguer** menu. Veillez à associer à l’instance de **DtsDebugHost.exe** répertorié en tant que **managé, x86** dans les **Type** colonne, pas à l’instance répertoriée en tant que **x86** uniquement.  
  
3.  Revenir au package en pause et continuer après le point d’arrêt ou cliquez sur **OK** pour fermer la boîte de message générée par la tâche de Script et continuer l’exécution du package et le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’objets personnalisés pour Integration Services](../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)   
 [Persistance des objets personnalisés](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)   
 [Outils de dépannage pour le développement des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  
