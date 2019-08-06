---
title: Installer Analysis Services exemples de données et de projets | Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c89ee3edf9338c4f74b0738d930ee74dbec7244
ms.sourcegitcommit: bcc3b2c7474297aba17b7a63b17c103febdd0af9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68794982"
---
# <a name="install-sample-data-and-multidimensional-projects"></a>Installer des exemples de données et des projets multidimensionnels 
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

Utilisez les instructions et les liens fournis dans cet article pour installer les fichiers de données et de projet utilisés dans les didacticiels de Analysis Services. 
  
## <a name="step-1-install-prerequisites"></a>Étape 1 : Prérequis à installer 
Les leçons du didacticiel supposent que vous avez installé les logiciels suivants. Vous pouvez installer toutes les fonctionnalités sur un seul ordinateur. Pour installer ces fonctionnalités, exécutez le programme d'installation de SQL Server et sélectionnez-les dans la page Sélection de fonctionnalités.  
  
-   Moteur de base de données SQL Server  
  
-   SQL Server Analysis Services (SSAS) 
  
    Analysis Services n’est disponible que dans les éditions suivantes: Evaluation, Enterprise, Business Intelligence, standard. Les modèles multidimensionnels ne sont pas pris en charge dans Azure Analysis Services.
  
    Par défaut, Analysis Services 2016 et versions ultérieures est installé en tant qu’instance tabulaire, que vous pouvez remplacer en choisissant le mode serveur multidimensionnel dans la page Configuration du serveur de l’Assistant Installation de.
  
## <a name="step-2-download-and-install-developer-and-management-tools"></a>Étape 2 : Télécharger et installer les outils de développement et de gestion
SQL Server Data Tools (SSDT) pour Visual Studio est téléchargé et installé séparément des autres fonctionnalités de SQL Server. Les concepteurs et les modèles de projet utilisés pour créer des modèles et des rapports DÉCISIONNELs sont inclus dans SSDT pour Visual Studio 2015 ou en tant que [packages NuGet](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) pour visual studio 2017.  
  
[Téléchargez SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=827542).   

SQL Server Management Studio (SSMS) est téléchargé et installé séparément des autres fonctionnalités de SQL Server.  

[Télécharger SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md)  

Éventuellement, installez Excel pour parcourir vos données multidimensionnelles pendant que vous suivez le didacticiel. L’installation d’Excel active la fonctionnalité **Analyser dans Excel** qui démarre Excel à l’aide d’une liste de champs de tableau croisé dynamique qui est connectée au cube que vous créez. Il est recommandé d'utiliser Excel pour parcourir les données, car vous pouvez rapidement créer un rapport de tableau croisé dynamique qui vous permet d'interagir avec les données.  
  
Sinon, vous pouvez parcourir les données à l'aide du concepteur de requêtes MDX intégré dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Le concepteur de requêtes retourne les mêmes données, sauf si les données sont présentées sous forme d'un ensemble de lignes à deux dimensions.  
  
## <a name="step-3-install-databases"></a>Étape 3 : Installer les bases de données  
Un modèle multidimensionnel Analysis Services utilise les données transactionnelles que vous importez d'un système de gestion de base de données relationnelle. Dans le cadre de ce didacticiel, vous utilisez la base de données relationnelle suivante comme source de données.  
  
-   **AdventureWorksDW2012 ou version ultérieure** : il s’agit d’un entrepôt de données relationnelles qui s’exécute sur une instance de moteur de base de données. Il fournit les données d’origine utilisées par les Analysis Services les bases de données et les projets que vous générez et déployez tout au long du didacticiel. Ce didacticiel part du principe que vous utilisez AdventureWorksDW2012. Toutefois, les versions ultérieures fonctionnent.
  
    Vous pouvez utiliser cet exemple de base [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] de données avec et versions ultérieures. En général, vous devez utiliser la version de l’exemple de base de données correspondant à votre version du moteur de base de données.
  
Pour installer la base de données, procédez comme suit:  
  
1.  Téléchargez une sauvegarde de base de données [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à partir de github.  
  
2.  Copiez le fichier de sauvegarde dans le répertoire de données de l’instance locale de Moteur de base de données SQL Server.
  
3.  Démarrez SQL Server Management Studio et connectez-vous à l'instance du moteur de base de données.  
  
4.  Restaurez la base de données.  
  
## <a name="step-4-grant-database-permissions"></a>Étape 4 : Accorder des autorisations de base de données  
Les exemples de projets utilisent les paramètres d'emprunt d'identité de source de données qui spécifient le contexte de sécurité dans lequel les données sont importées ou traitées. Par défaut, les paramètres d'emprunt d'identité spécifient le compte de service Analysis Services pour accéder aux données. Pour utiliser ce paramètre par défaut, vous devez vous assurer que le compte de service sous lequel Analysis Services s’exécute dispose des autorisations de lecteur de données sur la base de données **AdventureWorksDW** .  
  
> [!NOTE]  
> À des fins de formation, il est recommandé d'utiliser l'option d'emprunt d'identité du compte de service par défaut et d'accorder des autorisations de lecteur de données au compte de service dans SQL Server. Bien que d'autres options d'emprunt d'identité soient disponibles, toutes ne sont pas adaptées aux opérations de traitement. En particulier, l'option permettant d'utiliser les informations d'identification de l'utilisateur actuel n'est pas prise en charge pour le traitement.  
  
1.  Déterminez le compte de service. Utilisez le Gestionnaire de configuration SQL Server ou l'application de console Services pour afficher les informations du compte. Si vous installez Analysis Services comme instance par défaut à l’aide du compte par défaut, le service s’exécute en tant que **NT Service\MSSQLServerOLAPService**.  
  
2.  Dans Management Studio, connectez-vous à l'instance du moteur de base de données.  
  
3.  Développez le dossier Sécurité, cliquez avec le bouton droit sur Connexions, puis sélectionnez **Nouvelle connexion**.  
  
4.  Dans la page Général, dans Nom de connexion, tapez **NT Service\MSSQLServerOLAPService** (ou n’importe quel compte sous lequel le service s’exécute).  
  
5.  Cliquez sur **Mappage de l’utilisateur**.  
  
6.  Activez la case à cocher en regard de la base de données **AdventureWorksDW** . L’appartenance au rôle doit automatiquement inclure **db_datareader** et **public**. Cliquez sur **OK** pour accepter les valeurs par défaut.  
  
## <a name="step-5-install-projects"></a>Étape 5 : Installer des projets  

Le didacticiel inclut des exemples de projets afin de pouvoir comparer les résultats par rapport à un projet achevé, ou démarrer une leçon qui est plus loin dans la séquence.  
  
1.  Téléchargez [Adventure-Works-Multidimensional-Tutorial-Projects. zip](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services) à partir de la page Adventure works pour Analysis Services Samples sur GitHub.  
  
    Les projets du didacticiel fonctionnent [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour et versions ultérieures.  
  
2.  Déplacez le fichier .zip vers un dossier immédiatement en dessous du lecteur racine (par exemple, C:\Didacticiel). Cette étape atténue l’erreur «chemin d’accès trop long» qui se produit parfois si vous tentez de décompresser les fichiers dans le dossier téléchargements.  
  
3.  Décompressez les exemples de projets : cliquez avec le bouton droit sur le fichier et sélectionnez **Extraire tout**. Après avoir extrait les fichiers, vous devez avoir les dossiers leçon 1, 2, 3, 5, 6, 7, 8, 9, 10 terminé et début de la leçon 4. 
  
4.  Supprimez les autorisations de lecture seule sur ces fichiers. Cliquez avec le bouton droit sur le dossier parent, sélectionnez **Propriétés**, puis désactivez la case à cocher **en lecture seule**. Cliquez sur **OK**. Appliquez les modifications à ce dossier, ces sous-dossiers et fichiers.  

5.  Ouvrez le fichier solution (. sln) qui correspond à la leçon dans laquelle vous vous trouvez. Par exemple, dans le dossier nommé « Leçon 1 Terminée », vous ouvririez le fichier Analysis Services Tutorial.sln.  
  
6.  Déployez la solution pour vérifier que les autorisations de base de données et les informations d’emplacement du serveur sont correctement configurées.  
  
    Si Analysis Services et le moteur de base de données sont installés comme instance par défaut (MSSQLServer) et que tous les logiciels s’exécutent sur le même ordinateur, cliquez sur **Déployer la solution** pour créer et déployer l’exemple de projet sur l’instance Analysis Services locale. Pendant le déploiement, les données sont traitées (ou importées) à partir de la base de données **AdventureWorksDW** sur l’instance de moteur de base de données locale. Une nouvelle base de données Analysis Services est créée sur l’instance Analysis Services qui contient les données récupérées à partir de l’Moteur de base de données.  
  
    Si vous rencontrez des erreurs, examinez les étapes précédentes relatives à la configuration des autorisations relatives à la base de données. En outre, vous devrez peut-être modifier les noms de serveurs. Le nom de serveur par défaut est localhost. Si vos serveurs sont installés sur des ordinateurs distants ou en tant qu'instances nommées, vous devez remplacer la valeur par défaut de façon à utiliser un nom de serveur qui est valide pour votre installation. En outre, si les serveurs se trouvent sur des ordinateurs distants, vous devrez peut-être configurer le Pare-feu Windows pour autoriser l'accès aux serveurs.  
  
    Le nom du serveur pour la connexion au moteur de base de données est spécifié dans l'objet Source de données de la solution multidimensionnelle (Didacticiel Adventure Works), visible dans l'Explorateur de solutions.  
  
    Le nom du serveur pour la connexion à Analysis Services est spécifié dans l'onglet Déploiement des pages de propriétés du projet, également visible dans l'Explorateur de solutions.  
  
7.  Dans SQL Server Management Studio, connectez-vous à Analysis Services. Vérifiez qu’une base de données nommée **Didacticiel Analysis Services** s’exécute sur le serveur.  
  
## <a name="next-step"></a>Étape suivante  
Vous êtes maintenant prêt à utiliser le didacticiel. Pour plus d’informations sur la prise en main, consultez [Modélisation multidimensionnelle &#40;didacticiel Adventure Works&#41;](multidimensional-modeling-adventure-works-tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
[Configurer le Pare-feu Windows pour autoriser l’accès à Analysis Services](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[Configurer le Pare-feu Windows pour autoriser l'accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
