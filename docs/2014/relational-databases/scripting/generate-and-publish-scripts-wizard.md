---
title: Assistant Générer et publier des scripts
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.generatescriptswizard.setscriptingoptions.f1
- sql9.swb.generatescriptswizard.scriptwizarddescription.f1
- sql12.swb.generatescriptswizard.saveorpublishscripts.f1
- sql9.swb.generatescriptswizard.selectdatabase.f1
- sql9.swb.generatescriptswizard.scriptfileoption.f1
- sql12.swb.generatescriptswizard.advancedscriptingoptions.f1
- sql9.swb.generatescriptswizard.choosescriptoptions.f1
- sql12.swb.generatescriptswizard.summarypage.f1
- sql9.swb.generatescriptswizard.chooseviews.f1
- sql12.swb.generatescriptswizard.providerconfiguration.f1
- sql9.swb.generatescriptswizard.choosestoredprocedures.f1
- sql9.swb.generatescriptswizard.chooseobjecttypes.f1
- sql9.swb.generatescriptswizard.welcome.f1
- sql9.swb.generatescriptswizard.chooseudf.f1
- sql12.swb.generatescriptswizard.manageproviders.f1
- sql9.swb.generatescriptswizard.chooseuddt.f1
- sql12.swb.generatescriptswizard.advancedpublishingoptions.f1
- sql12.swb.generatescriptswizard.introduction.f1
- sql9.swb.generatescriptswizard.chooserules.f1
- sql12.swb.generatescriptswizard.chooseobjects.f1
- sql9.swb.generatescriptswizard.progress.f1
- sql9.swb.generatescriptswizard.choosedefaults.f1
- sql9.swb.generatescriptswizard.chooseobjects.f1
- sql9.swb.generatescriptswizard.choosetables.f1
helpviewer_keywords:
- databases [SQL Server], publishing
- publishing databases
- scripts [SQL Server], generating
- scripts [SQL Server], publishing
- databases [SQL Server], generating scripts
- Publish Database Wizard
ms.assetid: 5ee520ba-ec7e-4199-a441-189e9e264b37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47bf324dd757661a6f49f18b28f810c87ca1419e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75242112"
---
# <a name="generate-and-publish-scripts-wizard"></a>Assistant Générer et publier des scripts
  Vous pouvez utiliser l’ **Assistant Générer et publier des scripts** pour créer des scripts afin de transférer une base de données d’une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ou de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]vers une autre. Vous pouvez générer des scripts pour une base de données sur une instance du moteur de base de données dans votre réseau local ou à partir de [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Les scripts générés peuvent être exécutés sur une autre instance du moteur de base de données ou [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Vous pouvez également utiliser l'Assistant pour publier directement le contenu d'une base de données sur un service Web créé à l'aide des Services de publication de base de données. Vous pouvez créer des scripts pour une base de données entière ou les limiter à des objets spécifiques.  
  
1.  **Avant de commencer :**  [publication sur un service hébergé](#PubHostSvc), [autorisations](#Permissions)  
  
2.  **Pour générer ou publier un script à l’aide de :**  [l’Assistant générer et publier des scripts](#GenPubScriptWiz)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Les bases de données source et cible peuvent se trouver sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ou sur une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui exécute [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou une version ultérieure.  
  
###  <a name="PubHostSvc"></a>Publication sur un service hébergé  
 Outre pour la création de scripts, l' **Assistant Générer et publier des scripts** peut être utilisé pour publier une base de données sur un type spécifique de service Web SQL Server hébergé. Le SQL Server Hosting Toolkit fournit des Services de publication de base de données en tant que projet source partagé sur CodePlex. Le projet des Services de publication de base de données peut être utilisé par les fournisseurs d'hébergement Web pour générer un ensemble de services Web permettant aux clients de déployer facilement des bases de données sur le service Web. Pour plus d'informations sur le téléchargement du SQL Server Hosting Toolkit, consultez [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025)(en anglais).  
  
 Pour publier une base de données sur un service d'hébergement Web, sélectionnez l'option **Publier sur le service Web** dans la page de **Définir les options de script** de l'Assistant.  
  
###  <a name="Permissions"></a> Autorisations  
 L'autorisation minimale pour publier une base de données est l'appartenance au rôle de base de données fixe db_ddladmin sur la base de données d'origine. L'autorisation minimale pour publier un script de base de données sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au fournisseur d'hébergement est l'appartenance au rôle de base de données fixe db_ddladmin sur la base de données cible.  
  
 L'utilisateur doit fournir également un nom d'utilisateur et un mot de passe pour accéder à son compte de fournisseur d'hébergement pour publier avec l'Assistant. La base de données cible doit être créée au fournisseur d'hébergement avant de publier la base de données source. La publication remplace les objets dans cette base de données existante.  
  
##  <a name="GenPubScriptWiz"></a>Utilisation de l’Assistant générer et publier des scripts  
 **Pour générer un script de publication**  
  
1.  Dans l' **Explorateur d'objets**, développez le nœud pour l'instance qui contient la base de données devant faire l'objet d'un script.  
  
2.  Pointez sur **Tâches**, puis cliquez sur **Générer des scripts**.  
  
3.  Renseignez les boîtes de dialogue de l'Assistant :  
  
    -   [Page Introduction](#Introduction)  
  
    -   [Page Sélectionner les objets](#ChooseObjects)  
  
    -   [Page Définir les options de script](#SetScriptOpt)  
  
    -   [Page Options de script avancées](#AdvScriptOpt)  
  
    -   [Page Gérer les fournisseurs](#MgProviders)  
  
    -   [Page Options de publication avancées](#AdvPubOpts)  
  
    -   [Page Configuration du fournisseur](#ProvConfig)  
  
    -   [Page Résumé](#Summary)  
  
    -   [Page Enregistrer ou publier des scripts](#SavePubScripts)  
  
###  <a name="Introduction"></a> Page Introduction  
 Cette page décrit la procédure de création ou de publication d'un script.  
  
 **Ne plus afficher cette page** - Permet d’ignorer cette page la prochaine fois que vous démarrez l’ **Assistant Générer et publier des scripts**.  
  
 **>suivant** -passe à la page **choisir une méthode** .  
  
 **Annuler** -termine l’Assistant sans générer ou publier un script à partir de la base de données.  
  
###  <a name="ChooseObjects"></a>Page choisir des objets  
 Utilisez cette page pour choisir les objets que vous souhaitez inclure dans les scripts générés par cet Assistant. Dans la page suivante de l'Assistant, vous aurez la possibilité d'enregistrer ces scripts à l'emplacement de votre choix ou de les utiliser pour publier des objets de base de données sur un fournisseur d'hébergement Web distant sur lequel les [Services de publication de base de données SQL Server](https://go.microsoft.com/fwlink/?LinkId=142025)sont installés.  
  
 **Script-totalité de la base de données** -cliquez sur cette option pour générer des scripts pour tous les objets de la base de données et pour inclure un script pour la base de données elle-même.  
  
 **Sélectionner des objets de base de données spécifiques** - Cliquez sur cette option pour limiter l’action de l’Assistant à la génération de scripts uniquement pour les objets de la base de données que vous choisissez :  
  
-   **Objets de base de données** - Sélectionnez au moins un objet à inclure dans le script.  
  
-   **Sélectionner tout** - Coche toutes les cases disponibles.  
  
-   **Désélectionner tout** - Décoche toutes les cases. Vous devez ensuite activer au moins un objet de base de données pour poursuivre.  
  
###  <a name="SetScriptOpt"></a>Page définir les options de script  
 Utilisez cette page pour spécifier si vous souhaitez que l'Assistant enregistre les scripts à l'emplacement de votre choix ou les utilise pour publier des objets de base de données sur un fournisseur d'hébergement Web distant. Pour publier, vous devez avoir accès à un service Web installé à l'aide des Database Publishing Services.  
  
 **Options** : Si vous souhaitez que l’Assistant enregistre les scripts à un emplacement de votre choix, sélectionnez **enregistrer les scripts à un emplacement spécifique**. Vous pourrez exécuter les scripts ultérieurement sur une instance du moteur de base de données ou sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Si vous souhaitez que l'Assistant publie vos objets de base de données sur un fournisseur d'hébergement Web distant, sélectionnez **Publier sur le service Web**.  
  
 **Enregistrer les scripts à un emplacement spécifique-permet d'** enregistrer un ou plusieurs. Fichiers de script Transact-SQL à un emplacement que vous spécifiez.  
  
-   **Avancé** -permet d’afficher la boîte de dialogue **options de script avancées** dans laquelle vous pouvez sélectionner des options avancées pour générer des scripts.  
  
-   **Enregistrer dans le fichier** : permet d’enregistrer le script dans un ou plusieurs fichiers. Sql. Cliquez sur le bouton (**...**) pour spécifier le nom et l’emplacement du fichier. Activez la case à cocher **Remplacer le fichier existant** pour remplacer le fichier s'il en existe déjà un du même nom. Cliquez sur **Fichier unique** ou **Fichier unique par objet** pour spécifier comment les scripts doivent être générés. Cliquez sur **Texte Unicode** ou **Texte ANSI** pour spécifier le type de texte qui doit être utilisé dans le script.  
  
-   **Enregistrer dans le presse-papiers** -permet d’enregistrer le script Transact-SQL dans le presse-papiers.  
  
-   **Enregistrer dans une nouvelle fenêtre de requête** -permet de générer le script dans une fenêtre de l’éditeur de requête moteur de base de données. Si aucune fenêtre d'éditeur n'est ouverte, une nouvelle fenêtre d'éditeur s'ouvre comme cible du script.  
  
 **Publier sur le service Web** -permet de publier les objets que vous avez sélectionnés sur un service d’hébergement Web distant pour lequel vous avez configuré un fournisseur.  
  
-   **Gérer les fournisseurs** : affiche la boîte de dialogue **gérer les fournisseurs** . Utilisez la boîte de dialogue **Gérer les fournisseurs** pour ajouter, modifier et supprimer des fournisseurs d'hébergement. Chaque fournisseur spécifie les informations de connexion à un service d'hébergement Web, ainsi que les bases de données cibles sur ce service.  
  
-   **Avancé** -permet d’afficher la boîte de dialogue **options de publication avancées** dans laquelle vous pouvez sélectionner des options avancées pour la publication de scripts.  
  
-   **Fournisseur** : sélectionnez le fournisseur qui spécifie les informations de connexion pour le service d’hébergement Web qui héberge la base de données dans laquelle vous souhaitez publier les objets que vous avez sélectionnés. Vous devez avoir au moins un fournisseur dans la boîte de dialogue **Gérer les fournisseurs** pour pouvoir sélectionner un fournisseur.  
  
-   **Base de données cible** : sélectionnez la base de données cible dans laquelle vous souhaitez publier les objets que vous avez sélectionnés. Vous devez sélectionner un fournisseur avant de sélectionner une base de données cible.  
  
###  <a name="AdvScriptOpt"></a>Page Options de script avancées  
 Utilisez cette page pour spécifier la façon dont vous souhaitez que cet Assistant génère des scripts. De nombreuses options sont disponibles. Les options sont grisées si elles ne sont pas prises en charge par la version de SQL Server ou [!INCLUDE[ssSDS](../../includes/sssds-md.md)] spécifiée dans **Type de moteur de base de données**.  
  
 **Options** : spécifiez les options avancées en sélectionnant une valeur dans la liste des paramètres disponibles à droite de chaque option.  
  
 **Général** -les options suivantes s’appliquent à l’ensemble du script.  
  
-   **Remplissage ANSI** -comprend `ANSI PADDING ON` dans le script. La valeur par défaut est **true**.  
  
-   **Ajouter au fichier** -lorsque la **valeur est true**, ce script est ajouté au bas d’un script existant, spécifié sur la page définir les options de **script** . Lorsqu'elle a la valeur **False**, le nouveau script remplace un script précédent. La valeur par défaut est **False**.  
  
-   **Continuer le script en cas d’erreur** -lorsque la **valeur est true**, le script s’arrête lorsqu’une erreur se produit. Lorsqu'elle a la valeur **False**, l'exécution du script continue. La valeur par défaut est **False**.  
  
-   **Convertir les UDDT en types de base** : lorsque la **valeur est true**, les types de données définis par l’utilisateur (UDDT) sont convertis en types de données de base sous-jacents qui ont été utilisés pour les créer. Utilisez **True** lorsque l'UDDT n'existe pas dans la base de données où le script s'exécutera. Lorsque cette option a la valeur **False**, les UDDT sont utilisés. La valeur par défaut est **False**.  
  
-   **Générer un script pour les objets dépendants** -génère un script pour tout objet dont la présence est requise lorsque le script de l’objet sélectionné est exécuté. La valeur par défaut est **true**.  
  
-   **Inclure des en-têtes descriptifs** -lorsque la **valeur est true**, des commentaires descriptifs sont ajoutés au script en séparant le script en sections pour chaque objet. La valeur par défaut est **False**.  
  
-   **Inclure IF NOT EXISTS** -lorsque la **valeur est true**, le script inclut une instruction pour vérifier si l’objet existe déjà dans la base de données et ne tente pas de créer un nouvel objet si l’objet existe déjà. La valeur par défaut est **False**.  
  
-   **Inclure les noms** des contraintes système : lorsque la valeur est **false**, la valeur par défaut des contraintes qui ont été automatiquement nommées dans la base de données d’origine est automatiquement renommée sur la base de données cible. Lorsqu'elle a la valeur **True**, les contraintes ont le même nom sur les bases de données cible et d'origine.  
  
-   **Inclure des instructions non prises en charge** -lorsque la **valeur est false**, le script ne contient pas d’instructions pour les objets qui ne sont pas pris en charge sur la version de serveur ou le type de moteur sélectionné. Si la valeur est **True**, le script contient les objets non pris en charge. Chaque instruction concernant un objet non pris en charge sera accompagnée d'un commentaire stipulant que l'instruction doit être modifiée avant que le script puisse être exécuté sur la version de SQL Server ou le type de moteur sélectionné. La valeur par défaut est **False**.  
  
-   **Noms d’objets de qualification de schéma** : comprend le nom du schéma dans le nom des objets créés. La valeur par défaut est **true**.  
  
-   **Liaison de script** -génère un script pour lier les objets de règle et les objets par défaut. La valeur par défaut est **False**. Pour plus d’informations, consultez [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) et [CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql).  
  
-   **Classement de script** -comprend des informations de classement dans le script. La valeur par défaut est **False**. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../collations/collation-and-unicode-support.md).  
  
-   Valeurs **par défaut du script** : contient les objets par défaut utilisés pour définir les valeurs par défaut dans les colonnes de la table. La valeur par défaut est **true**. Pour plus d’informations, consultez [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
-   Créer un **script de suppression et de création** : [!INCLUDE[tsql](../../../includes/tsql-md.md)] lors de la création d’un **script**, des instructions sont incluses pour créer des objets. Lors de la suppression [!INCLUDE[tsql](../../../includes/tsql-md.md)] du **script**, les instructions sont incluses pour supprimer les objets. Avec **Générer un script de création/suppression (DROP/CREATE)**, l'instruction de suppression [!INCLUDE[tsql](../../../includes/tsql-md.md)] est incluse dans le script, suivie de l'instruction de création, pour chaque objet faisant l'objet d'un script. La valeur par défaut est **Générer un script de création (CREATE)**.  
  
-   Générer un script pour les **propriétés étendues** -inclut les propriétés étendues dans le script si l’objet a des propriétés étendues. La valeur par défaut est **true**.  
  
-   **Script pour le type de moteur** -crée un script qui peut être exécuté sur le type sélectionné [!INCLUDE[ssSDS](../../includes/sssds-md.md)] de ou d’une instance du moteur de base de données SQL Server. Les objets non pris en charge sur le type spécifié ne sont pas inclus dans le script. La valeur par défaut est le type du serveur d'origine.  
  
-   **Script pour la version du serveur** -crée un script qui peut être exécuté sur la version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sélectionnée de. Les fonctionnalités qui sont nouvelles dans une version ne peuvent pas faire l'objet d'un script pour les versions antérieures. La valeur par défaut est la version du serveur d'origine.  
  
-   **Connexions de script** : lorsque l’objet à scripter est un utilisateur de base de données, cette option crée les connexions dont l’utilisateur dépend. La valeur par défaut est **False**.  
  
-   Créer un **script des autorisations au niveau objet** -comprend des scripts pour définir l’autorisation sur les objets dans la base de données. La valeur par défaut est **False**.  
  
-   **Script Statistics** : lorsqu’elle est définie sur **script Statistics**, `CREATE STATISTICS` cette option comprend l’instruction permettant de recréer des statistiques sur l’objet. L'option **Générer un script des statistiques et des histogrammes** crée également des informations d'histogramme. La valeur par défaut est **Ne pas générer de script des statistiques**. Pour plus d’informations, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
-   **Script use Database** -ajoute l' `USE DATABASE` instruction au script. Pour vous assurer que les objets de base de données sont créés dans la base de données correcte, incluez l'instruction `USE DATABASE`. Lorsque le script est censé être utilisé dans une base de données différente, sélectionnez **false** pour `USE DATABASE` omettre l’instruction. La valeur par défaut est **true**. Pour plus d’informations, consultez [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   **Types de données à script** -sélectionne ce qui doit faire l’objet d’un script : **données uniquement**, **schéma uniquement**ou les deux. La valeur par défaut est **Schéma uniquement**.  
  
 **Options de table/vue** -les options suivantes s’appliquent uniquement aux scripts des tables ou des vues.  
  
-   **Suivi des modifications de script** -suivi des modifications de scripts s’il est activé sur la base de données d’origine ou sur les tables de la base de données d’origine. La valeur par défaut est **False**. Pour plus d’informations, consultez [À propos du suivi des modifications &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
-   **Contraintes de validation** de script `CHECK` : ajoute des contraintes au script. La valeur par défaut est **true**. Les contraintes `CHECK` exigent que les données entrées dans une table satisfassent à certaines conditions spécifiées. Pour plus d’informations, consultez [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
-   **Options de compression des données de script** : scripts de compression des données s’ils sont configurés sur la base de données d’origine ou sur les tables de la base de données d’origine. Pour plus d’informations, consultez [Data Compression](../data-compression/data-compression.md). La valeur par défaut est **False**.  
  
-   Générer un script pour les **clés étrangères** -ajoute des clés étrangères au script. La valeur par défaut est **true**. Les clés étrangères indiquent et garantissent les relations entre les tables.  
  
-   Générer un script pour les index de recherche en **texte intégral** -génère un script pour la création d’index de recherche en texte intégral. La valeur par défaut est **False**.  
  
-   **Script Indexes** -génère un script pour la création d’index. La valeur par défaut est **true**. Les index permettent de trouver rapidement des données.  
  
-   Générer un script pour les **clés primaires** -génère des scripts pour la création de clés primaires sur les tables. La valeur par défaut est **true**. Les clés primaires identifient de manière unique chaque ligne d'une table.  
  
-   **Déclencheurs de script** : génère des scripts pour la création de déclencheurs DML sur les tables. La valeur par défaut est **False**. Un déclencheur DML est une action programmée pour s'exécuter lorsqu'un événement de langage de manipulation de données (DML, Data Manipulation Language) se produit sur le serveur de base de données. Pour plus d'informations, consultez [DML Triggers](../triggers/dml-triggers.md).  
  
-   Générer un script pour les **clés uniques** -génère un script pour la création de clés uniques sur les tables. Les clés uniques empêchent l'entrée de données dupliquées. La valeur par défaut est **true**. Pour plus d’informations, consultez [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
###  <a name="MgProviders"></a>Page gérer les fournisseurs  
 Utilisez cette boîte de dialogue pour afficher, ajouter, modifier, supprimer ou tester les connexions des fournisseurs d'hébergement. Un fournisseur d'hébergement spécifie les informations de connexion pour un service Web créé à l'aide du projet de Service de publication de base de données dans le SQL Server Hosting Toolkit sur CodePlex.  
  
 **Fournisseurs configurés** : répertorie le nom et l’adresse du service **Web** de chaque fournisseur d’hébergement qui a été enregistré.  
  
 **Nouveau** : ouvre la boîte **de dialogue Configuration du fournisseur pour le nouveau fournisseur** pour ajouter un nouveau fournisseur d’hébergement.  
  
 **Modifier** -ouvre la boîte de dialogue **configuration du fournisseur** correspondante pour modifier un fournisseur d’hébergement existant.  
  
 **Supprimer** -supprime le fournisseur d’hébergement sélectionné.  
  
 **Test-teste** la connexion à un service d’hébergement à l’aide des informations du fournisseur sélectionné.  
  
 **OK** -enregistre toutes les modifications que vous avez apportées dans la boîte de dialogue **fournisseur d’hébergement** .  
  
 **Annuler-annule** toutes les modifications que vous avez apportées dans la boîte de dialogue **fournisseur d’hébergement** .  
  
###  <a name="AdvPubOpts"></a>Page Options de publication avancées  
 Utilisez cette page pour spécifier la façon dont vous souhaitez que cet Assistant publie une base de données. De nombreuses options sont disponibles. Les options sont grisées si elles ne sont pas prises en charge par la version de SQL Server ou [!INCLUDE[ssSDS](../../includes/sssds-md.md)] spécifiée dans **Type de moteur de base de données**.  
  
 **Options** : spécifiez les options avancées en sélectionnant une valeur dans la liste des paramètres disponibles à droite de chaque option.  
  
 **Général** -les options suivantes s’appliquent à l’ensemble de la publication.  
  
1.  **Convertir les UDDT en types de base** : lorsque la **valeur est true**, les types de données définis par l’utilisateur (UDDT) sont convertis en types de données de base sous-jacents qui ont été utilisés pour les créer. Utilisez **True** lorsque l'UDDT n'existe pas dans la base de données où le script s'exécutera. Lorsque cette option a la valeur **False**, les UDDT sont utilisés. La valeur par défaut est **False**.  
  
2.  **Publier le classement** -comprend les informations de classement pour les colonnes de table. La valeur par défaut est **False**. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../collations/collation-and-unicode-support.md).  
  
3.  **Publier les paramètres par défaut** : contient les objets par défaut utilisés pour définir les valeurs par défaut dans les colonnes de la table. La valeur par défaut est **true**. Pour plus d’informations, consultez [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
4.  **Publier les objets dépendants** -publie tout objet dont la présence est requise lorsque le script de l’objet sélectionné est exécuté. La valeur par défaut est **True**.  
  
5.  **Publier les propriétés étendues** -inclut les propriétés étendues dans le script envoyé au fournisseur pour la publication, si l’objet a des propriétés étendues. La valeur par défaut est **true**.  
  
6.  **Publier pour la version du serveur** -crée un script qui est envoyé au fournisseur distant pour la publication d’une façon qui peut être exécutée sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]version sélectionnée de. Les fonctionnalités qui sont nouvelles dans une version ne peuvent pas faire l'objet d'un script pour les versions antérieures. La valeur par défaut est la version du serveur d'origine.  
  
7.  **Publier les autorisations au niveau objet** : comprend les autorisations sur les objets sélectionnés dans la base de données. La valeur par défaut est **False**.  
  
8.  **Publier les statistiques** -quand elle est configurée pour publier `CREATE STATISTICS` des **statistiques**, comprend l’instruction pour recréer des statistiques sur l’objet. L'option **Publier les statistiques et les histogrammes** crée également des informations d'histogramme. La valeur par défaut est **Ne pas publier les statistiques**. Pour plus d’informations, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
9. **Publier les options vardecimal** -active `vardecimal` le format de table sur la table de base de données cible lorsqu’il est activé sur la table de base de données d’origine. La valeur par défaut est **true**.  
  
10. **Noms d’objets de qualification de schéma** : comprend le nom du schéma dans le nom des objets créés. La valeur par défaut est **true**.  
  
11. **Liaison de script** -comprend la liaison pour les objets de règle et les objets par défaut dans le script envoyé au fournisseur pour la publication. La valeur par défaut est **true**. Pour plus d’informations, consultez [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) et [CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql).  
  
12. **Types de données à publier** -sélectionne ce qui doit faire l’objet d’un script : **données uniquement**, **schéma uniquement**ou les deux. La valeur par défaut est **Schéma et données**.  
  
 **Options de publication** -spécifie s’il faut utiliser des transactions lors de la publication sur le fournisseur de l’hôte Web.  
  
1.  **Publier à l’aide** d’une transaction-utilise des transactions lors de la publication sur un fournisseur d’hébergement Web distant. Si la base de données cible ne peut pas terminer la publication, les transactions sont restaurées. La valeur par défaut est **true**.  
  
 **Options de table/vue** -les options suivantes s’appliquent uniquement aux tables ou aux vues.  
  
1.  **Publier les contraintes de validation** : comprend la `CHECK` création de contraintes dans le processus de publication. La valeur par défaut est **True**. Les contraintes `CHECK` exigent que les données entrées dans une table satisfassent à certaines conditions spécifiées. Pour plus d’informations, consultez [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
2.  **Publier les clés étrangères** -comprend la création de clés étrangères dans le processus de publication. La valeur par défaut est **true**. Les clés étrangères indiquent et garantissent les relations entre les tables. Pour plus d'informations, consultez [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
3.  Publier les index de recherche en **texte intégral** -génère un script pour la création d’index de recherche en texte intégral. La valeur par défaut est **False**.  
  
4.  **Publier des index** : comprend des index sur des tables dans le processus de publication. La valeur par défaut est **true**. Les index permettent de trouver rapidement des données.  
  
5.  **Publier les clés primaires** -comprend la création de clés primaires dans le processus de publication. La valeur par défaut est **True**. Les clés primaires identifient de manière unique chaque ligne d'une table. Pour plus d'informations, consultez [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
6.  **Publier les déclencheurs** -comprend la création de déclencheurs DML dans le processus de publication. La valeur par défaut est **true**. Un déclencheur DML est une action programmée pour s'exécuter lorsqu'un événement de langage de manipulation de données (DML, Data Manipulation Language) se produit sur le serveur de base de données. Pour plus d'informations, consultez [DML Triggers](../triggers/dml-triggers.md).  
  
7.  **Publier les clés uniques** -comprend la création de clés uniques sur les tables dans le processus de publication. Les clés uniques empêchent l'entrée de données dupliquées. La valeur par défaut est **true**. Pour plus d’informations, consultez [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
8.  **Publier le suivi des modifications** : comprend le suivi des modifications dans le processus de publication, s’il est activé sur la base de données d’origine ou sur les tables de la base de données d’origine. La valeur par défaut est **False**. Pour plus d’informations, consultez [À propos du suivi des modifications &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
9. **Publier les options de compression de données** -comprend des options de compression de données dans le processus de publication, si elles sont configurées sur la base de données d’origine ou sur les tables de la base de données d’origine. La valeur par défaut est **true**. Pour plus d’informations, consultez [Data Compression](../data-compression/data-compression.md).  
  
###  <a name="ProvConfig"></a>Page Configuration du fournisseur  
 Utilisez cette boîte de dialogue pour afficher ou modifier des paramètres de fournisseur d'hébergement. Cette boîte de dialogue permet d'effectuer les opérations suivantes :  
  
-   afficher, ajouter ou modifier les informations de connexion d'un fournisseur d'hébergement ;  
  
-   afficher, ajouter, modifier ou supprimer une base de données pour une connexion de fournisseur ;  
  
-   configurer automatiquement des bases de données pour un fournisseur d'hébergement.  
  
 Un fournisseur d'hébergement spécifie les informations de connexion pour un service Web créé à l'aide du projet de Service de publication de base de données dans le SQL Server Hosting Toolkit sur CodePlex.  
  
 **Nom** -nom du fournisseur d’hébergement.  
  
 **Adresse du service Web** -adresse https pour le service d’hébergement.  
  
 **Authentification du service Web** : nom d’utilisateur et mot de passe requis pour ouvrir une session sur le service d’hébergement.  
  
 **Enregistrer le mot de passe** -chiffrer et enregistrer le mot de passe sur votre ordinateur local.  
  
 **Bases de données disponibles** : les bases de données configurées pour les fournisseurs d’hébergement sont répertoriées par ordre croissant au format suivant : *SERVER_NAME*. *database_name*.  
  
 **Nouveau** : Ouvrez la boîte de dialogue configuration **de la base de données** et ajoutez une nouvelle base de données.  
  
 **Modifier** -ouvre la boîte de dialogue configuration **de la base** de données pour la base de données sélectionnée.  
  
 **Supprimer** -supprime la base de données sélectionnée.  
  
 **Définir comme valeur par défaut** : sélectionnez la base de données comme base de données par défaut.  
  
 **OK** -enregistrer toutes les modifications que vous avez apportées dans cette boîte de dialogue et revenir à l’Assistant.  
  
 **Annuler** -annule toutes les modifications que vous avez apportées dans cette boîte de dialogue et retourne à l’Assistant.  
  
###  <a name="Summary"></a>Page Résumé  
 Cette page résume les options que vous avez sélectionnées dans cet Assistant. Pour modifier une option, cliquez sur **Précédent**. Pour commencer à générer des scripts qui seront enregistrés ou publiés, cliquez sur **Suivant**.  
  
 **Vérifiez vos sélections** -affiche les sélections que vous avez effectuées pour chaque page de l’Assistant. Développez un nœud pour voir les options sélectionnées pour la page correspondante.  
  
###  <a name="SavePubScripts"></a>Page enregistrer ou publier des scripts  
 Utilisez cette page pour contrôler la progression de l'Assistant.  
  
 **Détails** -affiche la colonne **action** pour voir la progression de l’Assistant. Après avoir généré les scripts, l'Assistant les enregistre dans un fichier ou les utilise pour la publication sur un service Web, selon vos sélections. Lorsque chacune de ces étapes est terminée, cliquez sur la valeur dans la colonne **Résultat** pour afficher le résultat de l'étape correspondante.  
  
 **Enregistrer le rapport** -cliquez pour enregistrer les résultats de la progression de l’Assistant dans un fichier.  
  
 **Annuler** : cliquez pour fermer l’Assistant avant la fin du traitement ou si une erreur se produit.  
  
 **Terminer** : cliquez pour fermer l’Assistant une fois le traitement terminé ou si une erreur se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de SMO](../server-management-objects-smo/installing-smo.md)   
 [Copier des bases de données sur d’autres serveurs](../databases/copy-databases-to-other-servers.md)  
  
  
