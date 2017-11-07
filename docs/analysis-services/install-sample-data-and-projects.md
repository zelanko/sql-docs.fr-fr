---
title: "Installer les exemples de données et les projets | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: fc475b25-cbb2-408a-901f-9299299538c5
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64715dfd607a2216d03f7c0b3dbc1501718c546c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="install-sample-data-and-projects"></a>Installer les exemples de données et des projets 
Utilisez les instructions et les liens fournis dans cette rubrique pour installer tous les fichiers de données et de projet utilisés dans le didacticiel Analysis Services.  
  
## <a name="step-1-install-sql-server-software"></a>Étape 1 : installer SQL Server  
Les leçons du didacticiel supposent que vous avez installé les logiciels suivants. Tous les logiciels suivants sont installés à l'aide du support d'installation de SQL Server. Pour simplifier le déploiement, vous pouvez installer toutes les fonctionnalités sur un seul ordinateur. Pour installer ces fonctionnalités, exécutez le programme d'installation de SQL Server et sélectionnez-les dans la page Sélection de fonctionnalités. Pour plus d’informations, consultez [Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   Moteur de base de données  
  
-   Analysis Services  
  
    Analysis Services est disponible dans les éditions suivantes uniquement : Evaluation, Enterprise, Business Intelligence, Standard.  
  
    Notez que les éditions SQL Server Express n'incluent pas Analysis Services. [Téléchargez l’édition Evaluation](http://go.microsoft.com/fwlink/?LinkId=392824) si vous souhaitez tester le logiciel gratuitement.  
  
    Par défaut, Analysis Services est installé en tant qu'instance multidimensionnelle, que vous pouvez remplacer en choisissant le mode serveur tabulaire dans la page de configuration du serveur de l'Assistant Installation. Si vous souhaitez exécuter les deux modes serveur, réexécutez le programme d'installation de SQL Server sur le même ordinateur pour installer une seconde instance d'Analysis Services dans l'autre mode.  
  
-   SQL Server Management Studio  
  
Éventuellement, installez Excel pour parcourir vos données multidimensionnelles pendant que vous suivez le didacticiel. L’installation d’Excel active la fonctionnalité **Analyser dans Excel** qui démarre Excel à l’aide d’une liste de champs de tableau croisé dynamique qui est connectée au cube que vous créez. Il est recommandé d'utiliser Excel pour parcourir les données, car vous pouvez rapidement créer un rapport de tableau croisé dynamique qui vous permet d'interagir avec les données.  
  
Sinon, vous pouvez parcourir les données à l'aide du concepteur de requêtes MDX intégré dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Le concepteur de requêtes retourne les mêmes données, sauf si les données sont présentées sous forme d'un ensemble de lignes à deux dimensions.  
  
## <a name="step-2-download-sql-server-data-tools-for-visual-studio-2015"></a>Étape 2 : Télécharger SQL Server Data Tools pour Visual Studio 2015  
Dans cette version, SQL Server Data Tools est téléchargé et installé séparément des autres fonctionnalités SQL Server. Les concepteurs et les modèles de projets utilisés pour créer les modèles BI et des rapports sont disponibles en téléchargement web gratuit.  
  
-   [Téléchargez SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=827542). Le fichier est enregistré dans le dossier Téléchargements. Exécutez le programme d'installation pour installer l'outil.  
  
    Redémarrez l'ordinateur pour terminer l'installation.  
  
## <a name="step-3-install-databases"></a>Étape 3 : installer les bases de données  
Un modèle multidimensionnel Analysis Services utilise les données transactionnelles que vous importez d'un système de gestion de base de données relationnelle. Pour les besoins de ce didacticiel, vous allez utiliser la base de données relationnelle suivante comme source de données.  
  
-   **AdventureWorksDW2012** - Il s’agit d’un entrepôt de données relationnelles qui s’exécute sur une instance du moteur de base de données. Il fournit les données d'origine qui seront utilisées par les bases de données Analysis Services et les projets que vous générez et déployez tout au long du didacticiel.  
  
    Vous pouvez utiliser cet exemple de base de données avec [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
Pour installer cette base de données, procédez comme suit :  
  
1.  Téléchargez la base de données [AdventureWorkDW2012](http://go.microsoft.com/fwlink/p/?LinkID=221770) à partir de la page d’exemples de produits de Codeplex.  
  
    Le nom du fichier de base de données est AdventureWorksDW2012_Data.mdf. Le fichier devrait se trouver dans le dossier Téléchargements de votre ordinateur.  
  
2.  Copiez le fichier AdventureWorksDW2012_Data.mdf dans le répertoire de données de l'instance locale du moteur de base de données SQL Server. Par défaut, celui-ci se trouve dans le dossier C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data.  
  
3.  Démarrez SQL Server Management Studio et connectez-vous à l'instance du moteur de base de données.  
  
4.  Cliquez avec le bouton droit sur Bases de données, puis cliquez sur **Attacher**.  
  
5.  Cliquez sur **Ajouter**.  
  
6.  Sélectionnez le fichier de base de données **AdventureWorksDW2012_Data.mdf** , puis cliquez sur **OK**. Si le fichier n'est pas répertorié, accédez au dossier C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data pour vous assurer que le fichier y est.  
  
7.  Dans les détails de la base de données, supprimez l'entrée du journal. Le programme d'installation suppose que vous avez un fichier journal, mais l'exemple ne contient pas de fichier journal. Un nouveau fichier journal est créé automatiquement lorsque vous attachez la base de données. Sélectionnez le fichier journal et cliquez sur **Supprimer**, puis cliquez sur **OK** pour joindre uniquement le fichier de la base de données primaire.  
  
## <a name="step-4-grant-database-permissions"></a>Étape 4 : octroyer des autorisations relatives à la base de données  
Les exemples de projets utilisent les paramètres d'emprunt d'identité de source de données qui spécifient le contexte de sécurité dans lequel les données sont importées ou traitées. Par défaut, les paramètres d'emprunt d'identité spécifient le compte de service Analysis Services pour accéder aux données. Pour utiliser ce paramètre par défaut, vous devez vous assurer que le compte de service sous lequel s’exécute Analysis Services a des autorisations de lecteur de données sur la base de données **AdventureWorksDW2012** .  
  
> [!NOTE]  
> À des fins de formation, il est recommandé d'utiliser l'option d'emprunt d'identité du compte de service par défaut et d'accorder des autorisations de lecteur de données au compte de service dans SQL Server. Bien que d'autres options d'emprunt d'identité soient disponibles, toutes ne sont pas adaptées aux opérations de traitement. En particulier, l'option permettant d'utiliser les informations d'identification de l'utilisateur actuel n'est pas prise en charge pour le traitement.  
  
1.  Déterminez le compte de service. Utilisez le Gestionnaire de configuration SQL Server ou l'application de console Services pour afficher les informations du compte. Si vous installez Analysis Services comme instance par défaut à l’aide du compte par défaut, le service s’exécute en tant que **NT Service\MSSQLServerOLAPService**.  
  
2.  Dans Management Studio, connectez-vous à l'instance du moteur de base de données.  
  
3.  Développez le dossier Sécurité, cliquez avec le bouton droit sur Connexions, puis sélectionnez **Nouvelle connexion**.  
  
4.  Dans la page Général, dans Nom de connexion, tapez **NT Service\MSSQLServerOLAPService** (ou n’importe quel compte sous lequel le service s’exécute).  
  
5.  Cliquez sur **Mappage de l’utilisateur**.  
  
6.  Cochez la case en regard de la base de données **AdventureWorksDW2012** . L’appartenance au rôle doit automatiquement inclure **db_datareader** et **public**. Cliquez sur **OK** pour accepter les valeurs par défaut.  
  
## <a name="step-5-install-projects"></a>Étape 5 : installer les projets  
Le didacticiel inclut des exemples de projets afin de pouvoir comparer les résultats par rapport à un projet achevé, ou démarrer une leçon qui est plus loin dans la séquence.  
  
Le fichier projet pour la leçon 4 est particulièrement important, car il fournit la base non seulement de cette leçon, mais également de toutes les leçons suivantes. Contrairement aux fichiers projet précédents, où les étapes du didacticiel avaient pour résultat une copie exacte des fichiers projet terminés, l'exemple de projet de la leçon 4 inclut de nouvelles informations de modèle qui sont introuvables dans le modèle que vous avez généré au cours des leçons 1 à 3. La leçon 4 suppose que vous démarrez avec un exemple de fichier projet qui est disponible dans le téléchargement suivant.  
  
1.  Téléchargez le [didacticiel Analysis Services SQL Server 2012](http://go.microsoft.com/fwlink/p/?LinkID=221866) sur la page d’exemples de produits de Codeplex.  
  
    Les didacticiels 2012 sont valides pour la version de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
    le fichier « Analysis Services Tutorial SQL Server 2012.zip » sera enregistré dans le dossier Téléchargements sur votre ordinateur.  
  
2.  Déplacez le fichier .zip vers un dossier immédiatement en dessous du lecteur racine (par exemple, C:\Didacticiel). Cette étape diminue la probabilité de survenue de l'erreur « Chemin d'accès trop long » qui se produit parfois si vous tentez de décompresser les fichiers dans le dossier Téléchargements.  
  
3.  Décompressez les exemples de projets : cliquez avec le bouton droit sur le fichier et sélectionnez **Extraire tout**. Après avoir extrait les fichiers, les projets suivants doivent être installés sur votre ordinateur :  
  
    -   Leçon 1 terminée  
  
    -   Leçon 2 terminée  
  
    -   Leçon 3 terminée  
  
    -   Leçon 4 terminée  
  
    -   Début de la leçon 4  
  
    -   Leçon 5 terminée  
  
    -   Leçon 6 terminée  
  
    -   Leçon 7 terminée  
  
    -   Leçon 8 terminée  
  
    -   Leçon 9 terminée  
  
    -   Leçon 10 terminée  
  
4.  Supprimez les autorisations de lecture seule sur ces fichiers. Cliquez avec le bouton droit sur le dossier parent, « Didacticiel Analysis Services SQL Server 2012 », sélectionnez **Propriétés**, puis décochez la case **Lecture seule**. Cliquez sur **OK**. Appliquez les modifications à ce dossier, ces sous-dossiers et fichiers.  
  
5.  Démarrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
6.  Ouvrez le fichier solution (.sln) correspondant à la leçon que vous utilisez. Par exemple, dans le dossier nommé « Leçon 1 Terminée », vous ouvririez le fichier Analysis Services Tutorial.sln.  
  
7.  Déployez la solution pour vérifier que les autorisations relatives à la base de données et les informations d'emplacement du serveur sont configurées correctement.  
  
    Si Analysis Services et le moteur de base de données sont installés comme instance par défaut (MSSQLServer) et que tous les logiciels s’exécutent sur le même ordinateur, cliquez sur **Déployer la solution** pour créer et déployer l’exemple de projet sur l’instance Analysis Services locale. Durant le déploiement, les données seront traitées (ou importées) à partir de la base de données **AdventureWorksDW2012** sur l’instance du moteur de base de données locale. Une nouvelle base de données Analysis Services est créée sur l'instance Analysis Services qui contient les données récupérées du moteur de base de données.  
  
    Si vous rencontrez des erreurs, examinez les étapes précédentes relatives à la configuration des autorisations relatives à la base de données. En outre, vous devrez peut-être modifier les noms de serveurs. Le nom de serveur par défaut est localhost. Si vos serveurs sont installés sur des ordinateurs distants ou en tant qu'instances nommées, vous devez remplacer la valeur par défaut de façon à utiliser un nom de serveur qui est valide pour votre installation. En outre, si les serveurs se trouvent sur des ordinateurs distants, vous devrez peut-être configurer le Pare-feu Windows pour autoriser l'accès aux serveurs.  
  
    Le nom du serveur pour la connexion au moteur de base de données est spécifié dans l'objet Source de données de la solution multidimensionnelle (Didacticiel Adventure Works), visible dans l'Explorateur de solutions.  
  
    Le nom du serveur pour la connexion à Analysis Services est spécifié dans l'onglet Déploiement des pages de propriétés du projet, également visible dans l'Explorateur de solutions.  
  
8.  Dans SQL Server Management Studio, connectez-vous à Analysis Services. Vérifiez qu’une base de données nommée **Didacticiel Analysis Services** s’exécute sur le serveur.  
  
## <a name="next-step"></a>Étape suivante  
Vous êtes maintenant prêt à utiliser le didacticiel. Pour plus d’informations sur la prise en main, consultez [Modélisation multidimensionnelle &#40;didacticiel Adventure Works&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
[Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)  
[Configurer le pare-feu Windows pour autoriser l'accès à Analysis Services](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[Configurer le Pare-feu Windows pour autoriser l'accès à SQL Server](../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
  

