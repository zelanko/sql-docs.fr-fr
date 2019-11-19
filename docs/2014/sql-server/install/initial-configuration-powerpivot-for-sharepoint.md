---
title: Configuration initiale (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ba58e81cb802f3debe1c481443751de1947c595e
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798117"
---
# <a name="initial-configuration-powerpivot-for-sharepoint"></a>Configuration initiale (PowerPivot pour SharePoint)
  Utilisez les étapes de cette rubrique pour configurer une première installation de PowerPivot pour SharePoint. La façon la plus simple de configurer une installation initiale consiste à utiliser l'outil de configuration de PowerPivot. Il automatise toutes les étapes de configuration décrites ci-dessous.  
  
 Sinon, si vous souhaitez avoir davantage de contrôle sur la façon dont le serveur est configuré, vous pouvez utiliser l'Administration centrale et les informations de cette rubrique pour effectuer chaque étape individuellement.  
  
 
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Le serveur SharePoint doit avoir été installé à l'aide de l'option d'installation Batterie de serveurs du programme d'installation de SharePoint. Un serveur SharePoint autonome qui utilise une base de données intégrée n'est pas pris en charge. Pour plus d’informations, consultez [conseils pour l’utilisation des fonctionnalités de SQL Server bi dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
> [!IMPORTANT]  
>  SharePoint 2010 SP1 doit être installé avant de pouvoir configurer PowerPivot pour SharePoint, ou une batterie de serveurs SharePoint qui utilise un serveur de base de données [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Si vous n'avez pas encore installé le Service Pack, faites-le maintenant avant de commencer la configuration du serveur.  
  
 PowerPivot pour SharePoint doit être installé. Au minimum, la solution de batterie doit être déployée. Utilisez l'outil de configuration de PowerPivot ou le script PowerShell de PowerPivot pour déployer la solution de batterie de serveurs. Les instructions de cette étape sont fournies dans cette rubrique.  
  
 L'ordinateur doit être attaché à un domaine. Les comptes que vous spécifiez pour les services doivent être des comptes d'utilisateur de domaine. Au minimum, vous avez besoin d'un compte de domaine pour l'application de service PowerPivot. Si vous configurez des services supplémentaires (tel qu'Excel Services), vous devez avoir des comptes séparés pour chaque service que vous configurez.  
  
 Vous devez être administrateur de batterie de serveurs pour ajouter PowerPivot pour SharePoint à la batterie. Vous devez connaître le mot de passe pour ajouter des serveurs et des applications à la batterie.  
  
##  <a name="deploywsp"></a>Étape 1 : déployer des solutions PowerPivot  
 Il existe deux solutions qui doivent être installées et déployées : une solution de batterie de serveurs et une solution d'application Web.  
  
### <a name="install-and-deploy-the-farm-solution"></a>Installer et déployer la solution de batterie de serveurs
  
 Dans la version précédente, le programme d'installation de SQL Server a installé et a déployé la solution de batterie de serveurs. Dans cette version, vous devez utiliser l'outil de configuration de PowerPivot ou le script PowerShell pour déployer la solution de batterie de serveurs. Vous ne pouvez pas utiliser l'Administration centrale pour déployer la solution de batterie de serveurs. Il s'agit de la seule étape de la configuration de PowerPivot pour SharePoint qui ne peut pas être effectuée dans l'Administration centrale. Une fois que la solution de batterie de serveurs est déployée, vous pouvez utiliser l'Administration centrale et les étapes de cette rubrique pour configurer une installation de PowerPivot pour SharePoint.  
  
 Dans cette étape, vous exécutez PowerShell pour installer et déployer la solution de batterie de serveurs. Pour plus d’informations, consultez [configuration de PowerPivot à l’aide de Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).  
  
1.  Ouvrez SharePoint 2010 Management Shell à l'aide de l'option **Exécuter en tant qu'administrateur** .  
  
2.  Exécutez la première applet de commande :  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     L'applet de commande retourne le nom de la solution, son ID, et Deployed=False. À l'étape suivante, vous déploierez la solution.  
  
3.  Exécutez la deuxième applet de commande pour déployer la solution :  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
### <a name="deploy-the-web-application-solution"></a>Déployer la solution d’application Web
  
1.  Cliquez sur le bouton Démarrer, sélectionnez **tous les programmes**, sélectionnez **produits Microsoft SharePoint 2010**, puis sélectionnez **administration centrale de SharePoint 2010**.  
  
2.  Dans l'Administration centrale de SharePoint 2010, sous Paramètres système, cliquez sur **Gérer les solutions de la batterie**.  
  
     Deux packages de solution séparés doivent s'afficher : powerpivotfarm.wsp et powerpivotwebapp.wsp. La première solution (powerpivotfarm.wsp) doit déjà être déployée. Une fois qu'elle est déployée, il n'est plus nécessaire de la redéployer. La deuxième solution (powerpivotwebapp.wsp) est déployée pour l'Administration centrale, mais vous devez la déployer manuellement pour chaque application Web SharePoint qui prendra en charge l'accès aux données PowerPivot.  
  
3.  Cliquez sur **powerpivotwebapp.wsp**.  
  
4.  Cliquez sur **déployer la solution.**  
  
5.  Dans **déployer sur ?** , sélectionnez l’application Web SharePoint à laquelle vous souhaitez ajouter la prise en charge des fonctionnalités PowerPivot.  
  
6.  Cliquez sur **OK**.  
  
7.  Répétez ces opérations pour les autres applications Web SharePoint qui prendront également en charge l'accès aux données PowerPivot.  
  
##  <a name="Geneva"></a>Étape 2 : démarrer les services sur le serveur  
 Un déploiement PowerPivot pour SharePoint requiert que votre batterie de serveurs inclue les services suivants : les services de calcul Excel, le service Banque d'informations sécurisé et le service d'émission de jetons Revendications vers Windows.  
  
 Le service d'émission de jetons Revendications vers Windows est requis pour Excel Services et PowerPivot pour SharePoint. Il sert à établir la connexion à des sources de données externes à l'aide de l'identité Windows de l'utilisateur SharePoint actif. Ce service doit s'exécuter sur chaque serveur SharePoint ayant activé Excel Services ou PowerPivot pour SharePoint. Si le service n'est pas déjà démarré, vous devez le démarrer maintenant afin de permettre à Excel Services de transmettre les requêtes authentifiées au service système PowerPivot.  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les services sur le serveur**.  
  
2.  Activez le service d'émission de jetons Revendications vers Windows.  
  
3.  Démarrez les services de calcul Excel.  
  
4.  Démarrez le service Banque d'informations sécurisé.  
  
5.  Vérifiez que SQL Server Analysis Services et le service système SQL Server PowerPivot sont démarrés.  
  
##  <a name="createapp"></a>Étape 3 : créer une application de service PowerPivot  
 L'étape suivante consiste à créer une application de service PowerPivot.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Dans le ruban **Applications de service** , cliquez sur **Nouveau**.  
  
3.  Sélectionnez **SQL Server application de service PowerPivot**. Si cette option ne figure pas dans la liste, cela signifie que PowerPivot pour SharePoint n'est pas installé ou que la solution n'est pas déployée.  
  
4.  Dans la page **créer une application de service PowerPivot** , entrez un nom pour l’application. La valeur par défaut est PowerPivotServiceApplication\<nombre >. Si vous créez plusieurs applications de service PowerPivot, il est utile d'entrer un nom descriptif pour permettre aux autres administrateurs de savoir comment l'application est utilisée.  
  
5.  Dans Pool d'applications, créez un nouveau pool d'applications et sélectionnez un compte de sécurité pour lui. Un compte d'utilisateur de domaine est requis.  
  
6.  Dans **serveur de base de données**, choisissez un serveur de base de données sur lequel créer la base de données d’application de service. La valeur par défaut est l'instance du moteur de base de données SQL Server qui héberge les bases de données de configuration de la batterie de serveurs.  
  
7.  Dans **nom de la base de données**, la valeur par défaut est PowerPivotServiceApplication1_\<GUID >. Le nom de la base de données par défaut correspond au nom par défaut de l'application de service. Si vous avez entré un nom d'application de service unique, suivez une convention d'affectation des noms similaire pour la base de données afin de pouvoir les gérer ensemble.  
  
8.  Dans **Authentification de la base de données**, la valeur par défaut est Authentification Windows. Si vous choisissez **Authentification SQL**, reportez-vous au guide de l'administrateur SharePoint pour des recommandations concernant l'utilisation de ce type d'authentification dans un déploiement SharePoint.  
  
9. Activez la case à cocher **Ajouter le proxy de cette application de service PowerPivot au groupe de proxy par défaut.** Cette option permet d'ajouter la connexion à l'application de service au groupe de connexions de service par défaut. Vous devez avoir au moins une application de service PowerPivot dans le groupe de connexions par défaut.  
  
     Si une application de service PowerPivot est déjà répertoriée dans le groupe de connexions par défaut, n'ajoutez pas une deuxième application de service à ce groupe. L'ajout de deux applications de service du même type dans le groupe de connexions par défaut n'est pas une configuration prise en charge. Pour plus d’informations sur l’utilisation d’autres applications de service dans un groupe de connexions, consultez [connecter une application de service PowerPivot à une application Web SharePoint dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca).  
  
10. Cliquez sur **OK**. Le service s'affiche avec les autres services gérés dans la liste des applications de service de la batterie de serveurs.  
  
##  <a name="ExcelServ"></a>Étape 4 : activer Excel Services  
 PowerPivot pour SharePoint requiert Excel Services pour prendre en charge l'accès aux données PowerPivot dans la batterie de serveurs. Vous pouvez déterminer si Excel Services est déjà activé en vérifiant si Application Excel Services figure dans la liste des applications de service dans l'Administration centrale. Si Excel Services n'est pas répertorié, procédez comme suit pour l'activer.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Dans le ruban applications de service, dans créer, cliquez sur **nouveau**.  
  
3.  Sélectionnez **application Excel Services**.  
  
4.  Dans Créer une nouvelle application Excel Services, spécifiez un nom (par exemple, Application Excel Services).  
  
5.  Dans Pool d'applications, sélectionnez Créer un nouveau pool d'applications et donnez-lui un nom descriptif (par exemple, Pool d'applications Excel Services).  
  
6.  Dans Configurable, sélectionnez un compte d'utilisateur de domaine Windows pour l'identité de ce pool d'applications.  
  
7.  Conservez la case à cocher activée par défaut qui ajoute le proxy d'application de service à la liste des connexions de service par défaut.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez sur l'application Excel Services que vous venez de créer.  
  
10. Cliquez sur **emplacements de fichiers approuvés** . dans cette page, sélectionnez votre emplacement approuvé. (En général, il est listé comme **http://** dans la colonne adresse.) Pour vous assurer qu’Excel Services et le service PowerPivot ont accès au classeur, vous devez inclure SharePoint en tant qu’emplacement approuvé Excel Services. Le service système PowerPivot ne peut pas accéder aux classeurs stockés hors d'une batterie de serveurs SharePoint.  
  
11. Dans la zone Propriétés du classeur, affectez à **taille maximale du classeur** la valeur 50.  
  
12. Dans données externes, définissez **autoriser les données externes** sur **les bibliothèques de connexions de données approuvées et incorporées**. Ce paramètre est requis pour l'accès aux données PowerPivot dans un classeur.  
  
13. Désactivez la case à cocher **avertir lors** de l’actualisation des données pour autoriser les images d’aperçu de feuilles de calcul individuelles dans la Galerie PowerPivot. Si vous choisissez de laisser les paramètres d'avertissement et de classeur spécifier l'actualisation à l'ouverture, vous risquez d'obtenir une seule image d'aperçu de l'avertissement au lieu des pages de votre classeur.  
  
14. Cliquez sur **OK**.  
  
##  <a name="SSS"></a>Étape 5 : activer Service Banque d’informations sécurisé et configurer l’actualisation des données  
 PowerPivot pour SharePoint requiert le service Banque d'informations sécurisé pour stocker des informations d'identification et le compte d'exécution sans assistance pour l'actualisation des données. Vous pouvez déterminer si le service Banque d'informations sécurisé est déjà activé en vérifiant s'il s'affiche dans la liste des applications de service.  
  
> [!IMPORTANT]  
>  Si le service Banque d'informations sécurisé est activé, vous devez toutefois vérifier qu'une clé principale a été générée pour ce dernier. Pour obtenir des instructions, consultez « Deuxième partie : générer la clé principale », dans la procédure suivante.  
  
 Si le service Banque d'informations sécurisé n'est pas répertorié, suivez les étapes suivantes pour l'activer maintenant. En activant la Banque d'informations sécurisée, les auteurs de classeurs et les propriétaires de documents peuvent accéder à un choix plus vaste d'options de connexion à la source de données, lorsqu'ils planifient une actualisation des données de leurs classeurs publiés.  
  
##### <a name="part-1-enable-secure-store-service"></a>Première partie : activer le service Banque d'informations sécurisé  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Dans le ruban applications de service, dans créer, cliquez sur **nouveau**.  
  
3.  Sélectionnez **service Banque d’informations sécurisé**.  
  
4.  Dans la page **créer une application Banque d’enregistrement sécurisée** , entrez un nom pour l’application.  
  
5.  Dans **base de données**, spécifiez l’instance de SQL Server qui hébergera la base de données pour cette application de service. La valeur par défaut est l'instance du moteur de base de données SQL Server qui héberge les bases de données de configuration de la batterie de serveurs.  
  
6.  Dans **nom de la base de données**, entrez le nom de la base de données d’application de service. La valeur par défaut est Secure_Store_Service_DB_\<GUID >. Le nom par défaut correspond au nom par défaut de l'application de service. Si vous avez entré un nom d'application de service unique, suivez une convention d'affectation des noms similaire pour la base de données afin de pouvoir les gérer ensemble.  
  
7.  Dans **Authentification de la base de données**, la valeur par défaut est Authentification Windows. Si vous choisissez Authentification SQL, reportez-vous au guide de l'administrateur SharePoint pour des recommandations concernant l'utilisation de ce type d'authentification dans votre batterie de serveurs.  
  
8.  Dans pool d’applications, sélectionnez **créer un nouveau pool d’applications.** Spécifiez un nom descriptif qui permettra aux autres administrateurs de serveurs d'identifier la manière dont le pool d'applications est utilisé.  
  
9. Sélectionnez un compte de sécurité pour le pool d'applications. Spécifiez un compte géré pour utiliser un compte d'utilisateur de domaine.  
  
10. Acceptez les valeurs par défaut restantes, puis cliquez sur **OK.** . L'application de service apparaît avec les autres services gérés dans la liste des applications de service de la batterie de serveurs.  
  
##### <a name="part-2-generate-the-master-key"></a>Deuxième partie : générer la clé principale  
  
1.  Cliquez sur l'application de service Banque d'informations sécurisé dans la liste.  
  
2.  Dans le ruban applications de service, cliquez sur **gérer**.  
  
3.  Dans gestion des clés, cliquez sur **générer une nouvelle clé**.  
  
4.  Entrez une phrase secrète et confirmez-la. Elle sera utilisée pour ajouter d'autres applications de service Banque d'informations sécurisé partagé.  
  
5.  Cliquez sur **OK**.  
  
##### <a name="part-3-configure-the-unattended-powerpivot-data-refresh-account"></a>Troisième partie : configurer le compte d'actualisation des données PowerPivot sans assistance  
 La création d'un compte d'actualisation des données sans assistance pour l'accès aux données PowerPivot est souvent requise pour l'accès aux données externes pendant l'actualisation des données. Par exemple, si Kerberos n'est pas activé, vous devez créer un compte sans assistance que le service PowerPivot peut utiliser pour se connecter aux sources de données externes.  
  
 Pour obtenir des instructions sur la création du compte d’actualisation des données PowerPivot sans assistance ou sur d’autres informations d’identification stockées utilisées dans l’actualisation des données, consultez [configurer le compte &#40;d’actualisation&#41; des données PowerPivot sans assistance PowerPivot pour SharePoint](../../analysis-services/configure-unattended-data-refresh-account-powerpivot-sharepoint.md) et [configurer les &#40;informations&#41;d’identification stockées pour l’actualisation des données PowerPivot PowerPivot pour SharePoint](../../../2014/analysis-services/configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="Usage"></a>Étape 6 : activer la collecte des données d’utilisation  
 PowerPivot pour SharePoint utilise l'infrastructure de collecte des données d'utilisation de SharePoint pour rassembler les informations concernant l'utilisation de PowerPivot dans toute la batterie de serveurs. Bien que les données d'utilisation fassent toujours partie d'une installation de SharePoint, vous devrez peut-être les activer avant qu'elles puissent être utilisées. Pour obtenir des instructions, consultez [configurer la collecte &#40;des données d’utilisation pour PowerPivot pour SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint).  
  
##  <a name="Upload"></a>Étape 7 : augmenter la taille maximale du téléchargement pour les applications Web SharePoint et Excel Services  
 Étant donné que les classeurs PowerPivot peuvent être volumineux, vous pouvez augmenter la taille de fichier maximale. Il y a deux paramètres de taille de fichier à configurer : Taille maximale du téléchargement pour l'application Web, et Taille maximale du classeur dans Excel Services. La taille de fichier maximale définie doit avoir la même valeur dans les deux applications. Pour obtenir des instructions, consultez [configurer la taille &#40;maximale&#41;de téléchargement de fichiers PowerPivot pour SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint).  
  
##  <a name="activatePP"></a>Étape 8 : activer l’intégration des fonctionnalités PowerPivot pour les collections de sites  
 L'activation de fonctionnalités au niveau de la collection de sites met à la disposition de vos sites des pages et des modèles d'application, notamment des pages de configuration pour l'actualisation des données planifiée et des pages d'application pour la Galerie PowerPivot et les bibliothèques de flux de données.  
  
1.  Sur un site SharePoint, cliquez sur **Actions du site**.  
  
     Par défaut, les applications Web SharePoint sont accessibles via le port 80. Cela signifie que vous pouvez souvent accéder à un site SharePoint en entrant http://\<nom de l’ordinateur > pour ouvrir la collection de sites racine.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans Administration de la collection de sites, cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Faites défiler la page jusqu’à ce que vous trouviez la **fonctionnalité de collection de sites d’intégration PowerPivot**.  
  
5.  Cliquez sur **Activer**.  
  
6.  Répétez ces étapes pour les collections de sites supplémentaires en ouvrant chaque site et en cliquant sur **Actions du site**.  
  
 Pour plus d’informations, consultez [activer l’intégration des fonctionnalités PowerPivot pour les collections de sites dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca).  
  
##  <a name="bkmk_redist"></a>Étape 9 : installer la version SQL Server 2008 R2 du fournisseur OLE DB sur une instance SQL Server 2012 PowerPivot pour SharePoint  
 Si vous souhaitez exécuter les versions anciennes et plus récentes des classeurs PowerPivot côte à côte sur le même serveur, vous devez installer le fournisseur OLE DB Analysis Services fourni avec SQL Server 2008 R2 sur un serveur [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot pour SharePoint.  
  
 L'installation du fournisseur permettra aux classeurs qui référencent MSOLAP.4 dans la chaîne de connexion de données de fonctionner correctement sur un serveur [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot. L'installation du fournisseur OLE DB SQL Server 2008 R2 est une approche alternative à la mise à niveau des classeurs créés dans une version antérieure de PowerPivot pour Excel.  
  
 Vous pouvez télécharger le fournisseur à partir de [SQL Server page 2008 R2 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=159570). Recherchez **microsoft® fournisseur Analysis Services OLE DB pour microsoft® SQL Server® 2008 R2**, puis téléchargez le package x64 du programme d’installation de `SQLServer2008_ASOLEDB10.msi`.  
  
 Pour plus d’informations sur l’installation du fournisseur, y compris les étapes de vérification, consultez [installer les fournisseur Analysis Services OLE DB sur des serveurs SharePoint](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
##  <a name="verifyinstall"></a>Étape 10 : vérifier l’installation  
 Le traitement des requêtes PowerPivot dans la batterie de serveurs se produit lorsqu'un utilisateur ou une application ouvre un classeur Excel contenant des données PowerPivot. Au minimum, vous pouvez activer des pages sur les sites SharePoint pour vérifier que les fonctionnalités PowerPivot sont disponibles. Toutefois, pour une vérification complète, vous devez disposer d'un classeur PowerPivot que vous pouvez publier sur SharePoint et auquel vous pouvez accéder à partir d'une bibliothèque. Vous pouvez, à des fins de test, publier un classeur d'exemple contenant déjà des données PowerPivot et l'utiliser pour confirmer que l'intégration SharePoint est correctement configurée.  
  
 Pour vérifier l'intégration de PowerPivot avec un site SharePoint, procédez comme suit :  
  
1.  Dans un navigateur, ouvrez l'application Web que vous avez créée. Si vous avez utilisé des valeurs par défaut, vous pouvez spécifier http://\<le nom de votre ordinateur > dans l’adresse URL.  
  
2.  Vérifiez que l'accès aux données et les fonctionnalités de traitement de PowerPivot sont disponibles dans l'application. Pour cela, vous pouvez vérifier la présence de modèles de bibliothèque fournis par PowerPivot :  
  
    1.  Sur actions du site, cliquez sur **autres options.** ..  
  
    2.  Dans les bibliothèques, vous devriez voir **bibliothèque de flux de données** et **Galerie PowerPivot**. Ces modèles de bibliothèque sont fournis par la fonctionnalité PowerPivot et sont visibles dans la liste des bibliothèques si la fonctionnalité est intégrée correctement.  
  
 Pour vérifier l'accès aux données PowerPivot sur le serveur, procédez comme suit :  
  
1.  Téléchargez un classeur PowerPivot dans la Bibliothèque PowerPivot ou une autre bibliothèque SharePoint.  
  
2.  Cliquez sur le document pour l'ouvrir à partir de la bibliothèque.  
  
3.  Cliquez sur un segment ou filtrez les données pour démarrer une requête PowerPivot. Le serveur charge les données PowerPivot en arrière-plan et renvoie les résultats. À l'étape suivante, vous allez vous connecter au serveur pour vérifier que les données sont chargées et mises en cache.  
  
4.  Démarrez SQL Server Management Studio à partir du groupe de programmes Microsoft SQL Server 2008 R2 dans le menu Démarrer. Si cet outil n'est pas installé sur votre serveur, vous pouvez passer à la dernière étape pour confirmer la présence de fichiers mis en cache.  
  
5.  Dans Type de serveur, sélectionnez **Analysis Services**.  
  
6.  Dans nom du serveur, entrez **\<nom du serveur > \powerpivot**, où **\<nom-serveur >** est le nom de l’ordinateur sur lequel est installée l’PowerPivot pour SharePoint.  
  
7.  Cliquez sur **Se connecter**.  
  
8.  Dans l’Explorateur d’objets, cliquez sur **bases de données** pour afficher la liste des fichiers de données PowerPivot qui sont chargés.  
  
9. Sur le système de fichiers de l'ordinateur, vérifiez le dossier suivant pour déterminer si les fichiers sont mis en cache sur disque. La présence de fichiers mis en cache est une vérification supplémentaire que votre déploiement est opérationnel. Pour consulter le cache des fichiers, accédez au dossier \Program Files\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup.  
  
##  <a name="nextsteps"></a>Étapes consécutives à l’installation  
 Après avoir vérifié l'installation, terminez la configuration du service en créant une Galerie PowerPivot ou en ajustant certains paramètres de configuration. Pour exploiter au mieux les composants serveur que vous venez d'installer, vous pouvez télécharger [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] pour créer puis publier votre premier classeur PowerPivot.  
  
### <a name="install-data-providers-used-for-data-refresh"></a>Installer des fournisseurs de données utilisés pour l'actualisation des données  
 Si vous avez activé l'actualisation des données, le serveur aura besoin des mêmes fournisseurs de données pour l'accès aux données externes utilisés par l'application cliente PowerPivot pour importer les données d'origine (par exemple, si les données ont été importées originairement à l'aide d'un fournisseur 32 bits, l'actualisation des données côté serveur requerra également le fournisseur 32 bits lorsqu'elle accède à la même source de données externe). Pour plus d’informations, consultez [actualisation des données PowerPivot avec SharePoint 2010](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md).  
  
### <a name="install-adonet-data-services"></a>Installer ADO.NET Data Services  
 Vous devez installer ADO.NET Data Services 3.5 SP1 si vous voulez exporter des listes SharePoint en tant que flux de données. Pour obtenir des instructions, consultez [installer ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
### <a name="create-a-powerpivot-gallery"></a>Créer une bibliothèque Galerie PowerPivot  
 La bibliothèque Galerie PowerPivot est une bibliothèque qui inclut des options d'aperçu et de présentation pour consulter des classeurs PowerPivot sur un site SharePoint. L'utilisation de la bibliothèque Galerie PowerPivot pour publier et afficher des classeurs PowerPivot est recommandée pour sa fonction d'aperçu. De plus, si vous avez également déployé Reporting Services sur le même serveur SharePoint, une bibliothèque Galerie PowerPivot facilite la création de rapports. Vous pouvez lancer le Générateur de rapports à partir d'une bibliothèque Galerie PowerPivot pour baser un nouveau rapport sur un classeur PowerPivot publié. Pour plus d’informations sur la création et l’utilisation de la bibliothèque, consultez [créer et personnaliser la Galerie PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery) et [utiliser la Galerie PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/use-power-pivot-gallery).  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Créer des sites de confiance supplémentaires dans Excel Services  
 Vous pouvez ajouter des sites de confiance dans Excel Services pour varier les autorisations et les paramètres de configuration sur les sites qui fournissent des classeurs Excel et des données PowerPivot. Pour plus d'informations, consultez [Create a trusted location for PowerPivot sites in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration).  
  
### <a name="tune-configuration-settings"></a>Régler les paramètres de configuration.  
 Une application de service PowerPivot est créée à l'aide des propriétés et des valeurs par défaut. Vous pouvez modifier les paramètres de configuration d'applications de service individuelles, pour modifier la méthodologie d'allocation des requêtes, définir des délais d'attente de serveur, modifier les seuils des événements de rapport des réponses aux requêtes ou spécifier la durée de conservation des données d'utilisation. Pour plus d’informations sur la configuration dans l’administration centrale ou sur l’utilisation des fonctionnalités PowerPivot dans les applications Web SharePoint, consultez [administration et configuration du serveur PowerPivot dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
### <a name="install-powerpivot-for-excel-and-build-a-powerpivot-workbook"></a>Installer PowerPivot pour Excel et générer un classeur PowerPivot  
 Après avoir installé les composants serveur dans une batterie, vous pouvez créer votre premier classeur Excel 2010 qui utilise des données PowerPivot incorporées, puis le publier sur une bibliothèque SharePoint dans une application Web. Avant de pouvoir générer des classeurs Excel qui incluent des données PowerPivot, vous devez commencer par une installation d'Excel 2010, suivie du complément PowerPivot pour Excel qui étend Excel pour prendre en charge l'importation et l'enrichissement des données PowerPivot.  
  
### <a name="add-servers-or-applications"></a>Ajouter des serveurs ou des applications  
 Lorsque vous déployez la solution PowerPivot, l'intégration des fonctionnalités est activée au niveau de la collection de sites pour toutes les collections de sites dans l'application Web. À mesure que vous créez des applications Web, vous devez déployer la solution powerpivotwebapp sur chacune d'elles. Pour obtenir des instructions, consultez [déployer des solutions PowerPivot sur SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint).  
  
 En fonction de la façon dont vous configurez l'application de service PowerPivot, le service système PowerPivot sera ajouté au groupe de connexions par défaut, ce qui le rend disponible pour toutes les applications Web qui utilisent des connexions par défaut. Toutefois, si vous avez configuré vos applications Web pour utiliser des listes de connexions d'application de service personnalisées, vous devrez ajouter l'application de service PowerPivot à chaque application Web SharePoint pour laquelle vous souhaitez activer le traitement des données PowerPivot. Pour plus d’informations, consultez [connecter une application de service PowerPivot à une application Web SharePoint dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca).  
  
 Avec le temps, si vous déterminez que des capacités supplémentaires de stockage et de traitement des données sont nécessaires, ajoutez une deuxième instance de serveur PowerPivot pour SharePoint à la batterie de serveurs. La procédure d'installation est presque identique aux étapes que vous avez suivies pour ajouter le premier serveur, à part la manière de spécifier des noms d'instance et les informations sur le compte de service. Pour obtenir des instructions, consultez [liste de vérification du déploiement : montée en puissance parallèle en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Configurer des comptes de service PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts)   
 [Créez et configurez une application de service PowerPivot dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca)   
 [Déployer des solutions PowerPivot sur SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint)   
 [Activer l’intégration des fonctionnalités PowerPivot pour les collections de sites dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca)   
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
