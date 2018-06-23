---
title: Génération, déploiement et débogage d’objets personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a0264b74acc5d4665dbbbe48678ad75538002d5e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041857"
---
# <a name="building-deploying-and-debugging-custom-objects"></a>Génération, déploiement et débogage d'objets personnalisés
  Après avoir écrit le code d'un objet personnalisé pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez générer l'assembly, le déployer, l'intégrer dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour le rendre disponible dans les packages, le tester et le déboguer.  
  
##  <a name="top"></a> Étapes du processus de génération, déploiement et débogage d’un objet personnalisé pour Integration Services  
 Vous avez déjà écrit les fonctionnalités personnalisées de votre objet. À présent, vous devez les tester et les rendre disponibles aux utilisateurs. Les étapes sont très similaires pour tous les types d'objets personnalisés que vous pouvez créer pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Voici les étapes à suivre pour les générer, les déployer et les déboguer :  
  
1.  [Signez](#signing) l’assembly à générer à l’aide d’un nom fort.  
  
2.  [Générez](#building) l’assembly.  
  
3.  [Déployez](#deploying) l’assembly en le déplaçant ou en le copiant dans le dossier [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] approprié.  
  
4.  [Installez](#installing) l’assembly dans le Global Assembly Cache (GAC).  
  
     L'objet est automatiquement ajouté à la boîte à outils.  
  
5.  [Résolvez les problèmes](#troubleshooting) liés au déploiement, si nécessaire.  
  
6.  [Testez](#testing) et déboguez votre code.  
  
##  <a name="signing"></a> Signature de l’assembly  
 Lorsqu'un assembly est destiné à être partagé, il doit être installé dans le Global Assembly Cache. Une fois que l'assembly est ajouté au Global Assembly Cache, il peut être utilisé par des applications telles que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Une exigence du Global Assembly Cache stipule que l'assembly doit être signé avec un nom fort, lequel garantit qu'un assembly est globalement unique. Un assembly avec nom fort possède un nom qualifié complet qui comprend son nom, sa culture, sa clé publique et son numéro de version. Le runtime utilise ces informations pour rechercher l'assembly et le distinguer des autres assemblys portant le même nom.  
  
 Pour signer un assembly avec un nom fort, vous devez d'abord avoir ou créer une paire de clés publique/privée. Cette paire de clés de chiffrement publique et privée est utilisée au moment de la génération pour créer un assembly avec nom fort.  
  
 Pour plus d'informations sur les noms forts et sur les étapes à suivre pour signer un assembly, consultez les rubriques suivantes dans la documentation du Kit de développement logiciel [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] :  
  
-   Assemblys avec noms forts  
  
-   Création d'une paire de clés  
  
-   Signature d'un assembly avec un nom fort  
  
 Vous pouvez signer facilement votre assembly avec un nom fort dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] au moment de la génération. Dans la boîte de dialogue **Propriétés du projet**, sélectionnez l’onglet **Signature**. Sélectionnez l’option **Signer l’assembly** et indiquez le chemin du fichier de clé (.snk).  
  
##  <a name="building"></a> Génération de l’assembly  
 Après avoir signé le projet, vous devez générer ou regénérer le projet ou la solution en utilisant les commandes disponibles dans le menu **Générer** de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Votre solution peut contenir un projet séparé d' interface utilisateur personnalisée, lequel doit également être signé avec un nom fort et peut être généré en même temps.  
  
 La méthode la plus pratique pour effectuer les deux étapes suivantes, à savoir le déploiement de l'assembly et son installation dans le Global Assembly Cache, consiste à écrire le script de ces étapes sous la forme d'un événement post-build dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Les événements de génération sont disponibles sur la page **Compiler** des propriétés d’un projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et sur la page **Événements de génération** d’un projet C#. Le chemin complet est requis pour les utilitaires d’invite de commandes tels que **gacutil.exe**. Les guillemets sont requis à la fois autour des chemins d'accès qui contiennent des espaces et autour des macros telles que $(TargetPath) qui s'étendent aux chemins d'accès qui contiennent des espaces.  
  
 Voici un exemple de ligne de commande d'événement après génération pour un module fournisseur d'informations personnalisé :  
  
```  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)  
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)  
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\120\DTS\LogProviders "  
```  
  
##  <a name="deploying"></a> Déploiement de l’assembly  
 Le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] localise les objets personnalisés disponibles dans les packages en énumérant les fichiers trouvés dans une série de dossiers créés lors de l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Lorsque la valeur par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les paramètres d’installation sont utilisés, cet ensemble de dossiers se trouve sous **C:\Program Files\Microsoft SQL Server\120\DTS**. Toutefois si vous créez un programme d’installation pour votre objet personnalisé, vous devez vérifier la valeur de la **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\Setup\DtsPath** pour vérifier l’emplacement de cette clé de Registre dossier.  
  
 Vous pouvez placer l'assembly dans le dossier de deux manières :  
  
-   Déplacez ou copiez l'assembly compilé vers le dossier approprié après l'avoir généré. (Par commodité, vous pouvez inclure la commande de copie dans un événement après génération.)  
  
-   Générez directement l'assembly dans le dossier approprié.  
  
 Les dossiers de déploiement suivants sous **C:\Program Files\Microsoft SQL Server\120\DTS** sont utilisés pour les différents types d’objets personnalisés :  
  
|Objet personnalisé|Dossier de déploiement|  
|-------------------|-----------------------|  
|Tâche|Tâches|  
|Gestionnaire de connexions|Connexions|  
|Module fournisseur d'informations|LogProviders|  
|Composant de flux de données|PipelineComponents|  
  
> [!NOTE]  
>  Les assemblys sont copiés vers ces dossiers pour prendre en charge l'énumération des tâches, gestionnaires de connexions, etc. disponibles. Par conséquent, vous ne devez pas déployer des assemblys qui contiennent uniquement l'interface utilisateur personnalisée des objets personnalisés vers ces dossiers.  
  
##  <a name="installing"></a> Installation de l’assembly dans le Global Assembly Cache  
 Pour installer l’assembly de tâche dans le Global Assembly Cache (GAC), utilisez l’outil en ligne de commande **gacutil.exe** ou faites glisser les assemblys vers le répertoire `%system%\assembly`. Par commodité, vous pouvez également inclure l’appel de **gacutil.exe** dans un événement post-build.  
  
 La commande suivante installe un composant nommé *MyTask.dll* dans le GAC en utilisant **gacutil.exe**.  
  
 `gacutil /iF MyTask.dll`  
  
 Vous devez fermer et rouvrir le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] après avoir installé une nouvelle version de votre objet personnalisé. Si vous avez installé des versions antérieures de votre objet personnalisé dans le Global Assembly Cache, vous devez les supprimer avant d'installer la nouvelle version. Pour désinstaller un assembly, exécutez **gacutil.exe** et spécifiez le nom de l’assembly avec l’option `/u`.  
  
 Pour plus d'informations sur le Global Assembly Cache, consultez Global Assembly Cache Tool (Gactutil.exe) dans [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Tools.  
  
##  <a name="troubleshooting"></a> Résolution des problèmes liés au déploiement  
 Si votre objet personnalisé apparaît dans la **boîte à outils** ou la liste des objets disponibles, mais que vous n’êtes pas en mesure de l’ajouter à un package, essayez la procédure suivante :  
  
1.  Recherchez plusieurs versions de votre composant dans le Global Assembly Cache. S'il existe plusieurs versions du composant dans le Global Assembly Cache, il est possible que le concepteur ne soit pas en mesure de charger votre composant. Supprimez toutes les instances de l'assembly dans le Global Assembly Cache et ajoutez de nouveau l'assembly.  
  
2.  Assurez-vous qu'une seule instance unique de l'assembly existe dans le dossier de déploiement.  
  
3.  Actualisez la boîte à outils.  
  
4.  Attachez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à **devenv.exe** et définissez un point d’arrêt pour parcourir pas à pas votre code d’initialisation afin de vérifier qu’aucune exception ne se produit.  
  
##  <a name="testing"></a> Test et débogage du code  
 L’approche la plus simple pour déboguer les méthodes d’exécution d’un objet personnalisé consiste à démarrer **dtexec.exe** à partir de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] après avoir généré votre objet personnalisé et à exécuter un package qui utilise le composant.  
  
 Si vous souhaitez déboguer les méthodes du composant au moment du design, comme le `Validate` (méthode), ouvrez un package qui utilise le composant dans une deuxième instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]et l’attacher à son **devenv.exe** processus.  
  
 Si vous souhaitez également déboguer les méthodes d’exécution du composant lorsqu’un package est ouvert et en cours d’exécution dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], vous devez forcer une pause dans l’exécution du package afin de pouvoir également effectuer un attachement au processus **DtsDebugHost.exe**.  
  
#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a>Pour déboguer les méthodes d'exécution d'un objet à l'aide d'un attachement à dtexec.exe  
  
1.  Signez et générez votre projet dans la configuration de débogage, déployez-le et installez-le dans le Global Assembly Cache comme indiqué dans cette rubrique.  
  
2.  Sur le **déboguer** onglet de **propriétés du projet**, sélectionnez **démarrer le programme externe** en tant que le **Action de démarrage**, recherchez  **DTExec.exe**, qui est installé par défaut dans C:\Program Files\Microsoft SQL Server\120\DTS\Binn.  
  
3.  Dans la zone de texte **Options de ligne de commande**, sous **Options de démarrage**, entrez les arguments de ligne de commande requis pour exécuter un package qui utilise votre composant. Souvent, l'argument de ligne de commande sera consitué du commutateur /F[ILE] suivi du chemin d'accès et du nom du fichier .dtsx. Pour plus d’informations, voir [dtexec Utility](../packages/dtexec-utility.md).  
  
4.  Définissez des points d'arrêt dans le code source aux emplacements appropriés dans les méthodes d'exécution de votre composant.  
  
5.  Exécutez votre projet.  
  
#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a>Pour déboguer les méthodes de conception d'un objet personnalisé via un attachement aux outils de données SQL Server  
  
1.  Signez et générez votre projet dans la configuration de débogage, déployez-le et installez-le dans le Global Assembly Cache comme indiqué dans cette rubrique.  
  
2.  Définissez des points d'arrêt dans le code source aux emplacements appropriés dans les méthodes de conception de votre objet personnalisé.  
  
3.  Ouvrez une deuxième instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et chargez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient un package qui utilise l'objet personnalisé.  
  
4.  Dans la première instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], effectuez un attachement à la deuxième instance de **devenv.exe** dans laquelle le package est chargé en sélectionnant **Attacher au processus** dans le menu **Déboguer** de la première instance.  
  
5.  Exécutez le package à partir de la deuxième instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a>Pour déboguer les méthodes d'exécution d'un objet personnalisé via un attachement aux outils de données SQL Server  
  
1.  Après avoir effectué les étapes répertoriées dans la procédure précédente, forcez une pause dans l’exécution de votre package afin de pouvoir effectuer un attachement à **DtsDebugHost.exe**. Vous pouvez forcer cette pause en ajoutant un point d'arrêt à l'événement `OnPreExecute` ou en ajoutant une tâche de script à votre projet et en entrant un script qui affiche un message modal.  
  
2.  Exécutez le package. Lorsque la pause se produit, basculez vers l’instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dans laquelle votre projet de code est ouvert et sélectionnez **Attacher au processus** dans le menu **Déboguer**. Assurez-vous d’effectuer l’attachement à l’instance de **DtsDebugHost.exe** répertoriée sous le nom **Managé, x86** dans la colonne **Type**, et non à l’instance répertoriée sous le nom **x86** seulement.  
  
3.  Revenez au package mis en pause et passez le point d’arrêt, ou cliquez sur **OK** pour fermer le message généré par la tâche de script, puis continuez l’exécution et le débogage du package.  
  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**restent jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’objets personnalisés pour Integration Services](developing-custom-objects-for-integration-services.md)   
 [Persistance des objets personnalisés](persisting-custom-objects.md)   
 [Outils de dépannage pour le développement des packages](../troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  