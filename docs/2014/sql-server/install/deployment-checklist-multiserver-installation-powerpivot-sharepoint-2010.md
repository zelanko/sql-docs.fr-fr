---
title: 'Liste de vérification de déploiement : Installation à plusieurs serveurs de PowerPivot pour SharePoint 2010 | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4380040a-1368-4a47-8930-47c65a192e59
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ae1d09ddc1df0d4ff33808c92b708f92b4f4820c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240529"
---
# <a name="deployment-checklist-multi-server-installation-of-powerpivot-for-sharepoint-2010"></a>Liste de vérification du déploiement : Installation à plusieurs serveurs de PowerPivot pour SharePoint 2010
  Cette liste de vérification vous guide tout au long des étapes d’ajout de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint à une batterie SharePoint 2010 à trois niveaux qui vous accumulez d’à partir de zéro. Une batterie de serveurs à trois niveaux comprend un niveau de base de données, un niveau applicatif et un niveau Web. Ajout de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] à cette topologie nécessite que vous exécutez le programme d’installation de SQL Server pour installer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur la couche application. Les fichiers programme PowerPivot sont ajoutés à la couche web, mais uniquement comme une tâche consécutive à l’installation lorsque vous la déployer solution d’application web. Bien que le déploiement comporte des étapes, il n'y a pas d'étape d'installation distincte à effectuer sur la couche Web ou la couche de données. Est la seule étape d’installation dont vous avez besoin pour effectuer l’installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur les serveurs d’applications.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez être administrateur local pour installer SQL Server et SharePoint 2010.  
  
 La personne qui installe SharePoint doit également configurer la batterie de serveurs. Pour configurer la batterie de serveurs, vous devez avoir un compte de connexion SQL Server sur le serveur de base de données. La connexion doit être affectée aux rôles suivants : `dbcreator`, `securityadmin` et `public`.  
  
 Vous devez disposer de SharePoint Server 2010 Enterprise Edition ou Evaluation Edition.  
  
 L'ordinateur doit être attaché à un domaine.  
  
 Vous devez savoir quels comptes vous utiliserez pour exécuter le moteur de base de données, les services de votre batterie et Analysis Services en mode intégré SharePoint. Bien que vous puissiez modifier ces comptes ultérieurement, vous les spécifierez pour la première fois pendant l'installation.  
  
 Les comptes de services que vous spécifiez pendant l'installation doivent être des comptes d'utilisateurs de domaine.  
  
 Avant de commencer l'installation, vérifiez les paramètres de votre navigateur pour vous assurer que vous disposez d'une connexion Internet. Le programme d'installation préalable ouvre une connexion Internet pour télécharger les logiciels requis. Vous devez procéder aux modifications suivantes pour vérifier que vous obtenez tous les logiciels nécessaires :  
  
-   Dans le Gestionnaire de serveurs, désactivez temporairement la Configuration de sécurité renforcée d'Internet Explorer pour autoriser des téléchargements sur le serveur. Pour les besoins du téléchargement des logiciels requis, vous pouvez vous contenter de désactiver IE ESC pour les administrateurs uniquement.  
  
-   Vous devrez peut-être également configurer Internet Explorer de manière qu'il ignore les serveurs proxy afin d'autoriser l'accès localhost aux URL Internet.  
  
    1.  Dans Internet Explorer, dans le menu Outils, cliquez sur Options Internet.  
  
    2.  Sous l'onglet Connexions, dans la zone Paramètres du réseau local, cliquez sur les paramètres réseau.  
  
    3.  Dans la zone de configuration automatique, désactivez la case à cocher Détecter automatiquement les paramètres de connexion.  
  
    4.  Dans la zone Serveur proxy, sélectionnez la case à cocher Utiliser un serveur proxy pour votre réseau local.  
  
    5.  Tapez l'adresse du serveur proxy dans la zone Adresse.  
  
    6.  Tapez le numéro de port du serveur proxy dans la case Port.  
  
    7.  Sélectionnez la case à cocher Ne pas utiliser de serveur proxy pour les adresses locales.  
  
    8.  Cliquez sur OK pour fermer la boîte de dialogue Paramètres du réseau local.  
  
    9. Cliquez sur OK pour fermer la boîte de dialogue Options Internet.  
  
##  <a name="installdb"></a> Installer un serveur de base de données  
 Cette rubrique suppose que votre topologie de batterie de serveurs est basée sur celle décrite dans l’article [plusieurs serveurs pour une batterie de serveurs à trois niveaux](http://go.microsoft.com/fwlink/?LinkId=182771). Si vous disposez déjà d’une batterie de serveurs est opérationnel, passez directement à [installer PowerPivot pour SharePoint](#installppapp).  
  
 Si vous venez de démarrer votre topologie, commencez par installer un moteur de base de données SQL Server. Ces instructions aboutissent à la création d'un serveur de base de données accessible depuis les serveurs SharePoint de votre batterie.  
  
1.  Sur l’ordinateur que vous utilisez pour le serveur de base de données, exécutez le programme d’installation de SQL Server pour installer le moteur de base de données SQL Server (consultez [installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)).  
  
     Au moment de sélectionner les composants à installer, choisissez les éléments suivants :  
  
    -   Services Moteur de base de données  
  
    -   Connectivité des outils clients  
  
    -   Outils d'administration - Complet (Basic sera inclus automatiquement)  
  
2.  Une fois le moteur de base de données installé, activez TCP/IP pour les connexions distantes et redémarrez le service :  
  
    1.  Démarrez le Gestionnaire de configuration SQL Server.  
  
    2.  Ouvrez Configuration du réseau SQL Server.  
  
    3.  Sélectionnez **Protocoles pour MSSQLSERVER**.  
  
    4.  Avec le bouton droit **TCP/IP** et sélectionnez **activer**.  
  
    5.  Cliquez sur **SQL Server Services**.  
  
    6.  Avec le bouton droit **SQL Server (MSSQLSERVER)**, puis cliquez sur **redémarrer**.  
  
3.  Autorisez l'accès entrant au serveur de base de données via le Pare-feu Windows. Cela permet aux serveurs SharePoint de la batterie de se connecter aux bases de données SharePoint. Pour plus d’informations, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
    1.  Dans le panneau de Windows, dans Outils d’administration, cliquez sur **pare-feu Windows avec fonctions avancées de sécurité**.  
  
    2.  Cliquez sur **règles de trafic entrant**.  
  
    3.  Cliquez sur **nouvelle règle**.  
  
    4.  Dans le Type de règle, cliquez sur **personnalisé**.  
  
    5.  Cliquez sur **Suivant**.  
  
    6.  Dans le programme, dans la section Services, cliquez sur **personnaliser**.  
  
    7.  Cliquez sur **appliquer à ce service**.  
  
    8.  Sélectionnez **SQL Server (MSSQLSERVER)** si votre installation de SQL Server en tant que l’instance par défaut, puis cliquez sur **OK**.  
  
    9. Cliquez sur **Suivant**.  
  
    10. Dans protocole et Ports, acceptez les paramètres par défaut et cliquez sur **suivant**.  
  
    11. Dans la portée, acceptez les paramètres par défaut et cliquez sur **suivant**.  
  
    12. Dans Action, acceptez les paramètres par défaut et cliquez sur **suivant**.  
  
    13. Dans profil, désactivez les cases à cocher pour **privé** et **Public**, puis cliquez sur **suivant**.  
  
    14. Dans nom, tapez un nom descriptif pour la règle de trafic entrant (par exemple, **SQL Server**).  
  
    15. Cliquez sur **Terminer**.  
  
##  <a name="installsp"></a> Installer et configurer une batterie de serveurs SharePoint 2010 à trois niveaux  
 Exécutez sur chacun des ordinateurs que vous utilisez comme serveurs SharePoint le programme d'installation des composants requis de SharePoint, puis le programme d'installation de SharePoint Server.  
  
 Utilisez les instructions suivantes de la documentation SharePoint 2010 pour installer et configurer une batterie de serveurs SharePoint 2010 comprenant deux serveurs Web et un serveur d'applications :  
  
 [Plusieurs serveurs pour une batterie de serveurs à trois niveaux (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=182771)  
  
 Lorsque vous êtes invité à spécifier un serveur de base de données, spécifiez celui que vous avez déjà installé.  
  
 Les procédures qui suivent supposent que vous avez configuré la batterie de serveurs en suivant les instructions prévues pour l'installation d'une batterie à trois niveaux. La batterie de serveurs doit inclure les services et fonctionnalités suivants :  
  
-   Excel Services, le service de recherche et le service Banque d'informations sécurisé ;  
  
-   une application Web et une collection de sites ;  
  
-   une collection de données d'utilisation et d'intégrité ;  
  
-   la journalisation des diagnostics.  
  
##  <a name="installppapp"></a> Installer PowerPivot pour SharePoint sur un serveur d’applications  
 Exécutez le programme d'installation de SQL Server pour ajouter PowerPivot pour SharePoint à une batterie de serveurs SharePoint. Si la batterie est composée de plusieurs serveurs SharePoint, vous devez exécuter le programme d'installation de SQL Server sur un serveur d'applications déjà joint à la batterie.  
  
 Installez toujours PowerPivot pour SharePoint sur un serveur d'applications. Bien que les serveurs Web frontaux exécutent également PowerPivot pour les composants serveur SharePoint, les composants qui s'exécutent sur le Web frontal sont installés pendant l'étape de configuration de PowerPivot pour SharePoint, lorsque vous déployez des solutions dans la batterie. Pour plus d’informations sur le programme d’installation, consultez [installer PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md).  
  
 Si votre topologie de déploiement appelle deux instances de PowerPivot pour SharePoint, exécutez le programme d'installation de SQL Server sur chaque serveur d'applications. Vous ne pouvez avoir qu'une seule instance de PowerPivot pour SharePoint sur un même ordinateur. Si vous avez besoin de plusieurs instances, vous devez utiliser des serveurs supplémentaires. Pour plus d’informations sur l’ajout de plusieurs serveurs PowerPivot pour SharePoint à la même batterie de serveurs, consultez [liste de vérification de déploiement : montée en puissance en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
##  <a name="installclientlib"></a> Installer les bibliothèques clientes Analysis Services sur les serveurs d’applications SharePoint qui n’ont pas d’une installation de PowerPivot pour SharePoint  
 Une topologie de batterie de serveurs qui inclut un serveur Web frontal ou un serveur d'applications exécutant les applications suivantes, sans installation de PowerPivot pour SharePoint sur le même ordinateur, requiert des logiciels supplémentaires pour prendre en charge les fonctionnalités et l'accès aux données PowerPivot :  
  
-   Excel Services ou PerformancePoint Services  
  
-   Administration centrale, exécutée comme application autonome sur son propre serveur  
  
 Excel Services et PerformancePoint Services requièrent tous les deux une version plus récente du fournisseur OLE DB Analysis Services pour prendre en charge l'accès aux données PowerPivot. Si vous exécutez l'une ou l'autre application sur un ordinateur qui ne dispose pas du fournisseur OLE DB le plus récent, vous devez installer le fournisseur manuellement. Pour plus d’informations, consultez [installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 De la même manière, un ordinateur qui comporte juste l'Administration centrale, sans PowerPivot pour SharePoint sur le même ordinateur, requiert la bibliothèque cliente ADOMD.NET. Cette bibliothèque est utilisée par le tableau de bord de gestion PowerPivot pour accéder aux données internes servant à remplir le tableau de bord. Pour plus d’informations, consultez [Installer ADOMD.NET sur des serveurs web frontaux exécutant l’Administration centrale](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).  
  
##  <a name="configsrvr"></a> Configurer le serveur  
 Utilisez l'outil de configuration de PowerPivot pour configurer PowerPivot pour SharePoint. L'outil analyse la configuration existante de la batterie et fournit des options d'installation ou d'activation des fonctionnalités SharePoint requises par PowerPivot pour SharePoint. Au cours de cette étape, le service d'émission de jetons Revendications vers Windows est démarré. De plus, si d'autres fonctionnalités SharePoint requises ne sont pas encore activées, l'outil de configuration les ajoute à la liste et inclut des actions pour activer la fonctionnalité.  
  
 Pour plus d’informations, consultez [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de Configuration PowerPivot&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md).  
  
##  <a name="AAM"></a> Configurer le mappage des accès de substitution pour les serveurs Web frontaux  
 Pour que les demandes d'accès aux données ou d'actualisation des données PowerPivot soient gérées par chaque serveurWeb frontal, vous devez mapper les différentes URL de chaque serveur à la même application Web.  
  
1.  Dans l’Administration centrale, sous gestion des applications, cliquez sur **configurer les mappages des accès de substitution**.  
  
2.  Dans Collection de mappages des accès de substitution, sélectionnez votre application Web.  
  
3.  Cliquez sur **ajouter une URL interne**.  
  
4.  Spécifiez l'URL du premier serveur Web frontal.  
  
5.  Répétez les étapes précédentes pour ajouter l'URL du deuxième serveur Web frontal.  
  
##  <a name="activatePP"></a> Activer la fonctionnalité d’intégration PowerPivot pour les Collections de sites  
 L'activation de fonctionnalités au niveau de la collection de sites met à la disposition de vos sites des pages et des modèles d'application, notamment des pages de configuration pour l'actualisation des données planifiée et des pages d'application pour la Galerie PowerPivot et les bibliothèques de flux de données.  
  
 L'outil de configuration de PowerPivot active l'intégration de fonctionnalité pour la collection de sites indiquée. Vous pouvez exécuter l'outil plusieurs fois pour sélectionner des collections de sites supplémentaires. Les administrateurs de site peuvent également configurer l'activation de fonctionnalités à partir de SharePoint. Pour plus d’informations, consultez [activer fonctionnalité d’intégration PowerPivot pour les Collections de sites dans l’Administration centrale](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md).  
  
##  <a name="verify"></a> Vérifier la disponibilité de l’intégration et le serveur  
 Le traitement des requêtes PowerPivot dans la batterie de serveurs se produit lorsqu'un utilisateur ou une application ouvre un classeur Excel contenant des données PowerPivot. Au minimum, vous pouvez activer des pages sur les sites SharePoint pour vérifier que les fonctionnalités PowerPivot sont disponibles. Toutefois, pour une vérification complète, vous devez disposer d'un classeur PowerPivot que vous pouvez publier sur SharePoint et auquel vous pouvez accéder à partir d'une bibliothèque. Vous pouvez, à des fins de test, publier un classeur d'exemple contenant déjà des données PowerPivot et l'utiliser pour confirmer que l'intégration SharePoint est correctement configurée.  
  
 Pour vérifier l'intégration de PowerPivot avec un site SharePoint, procédez comme suit :  
  
1.  Dans un navigateur, ouvrez l'application Web que vous avez créée. Si vous avez utilisé les valeurs par défaut, vous pouvez spécifier http://\<votre nom d’ordinateur > dans l’adresse URL.  
  
2.  Vérifiez que l'accès aux données et les fonctionnalités de traitement de PowerPivot sont disponibles dans l'application. Pour cela, vous pouvez vérifier la présence de modèles de bibliothèque fournis par PowerPivot :  
  
    1.  Dans Actions du Site, cliquez sur **plus d’Options...** .  
  
    2.  Dans les bibliothèques, vous devez voir **bibliothèque de flux de données** et **galerie PowerPivot**. Ces modèles de bibliothèque sont fournis par la fonctionnalité PowerPivot et sont visibles dans la liste des bibliothèques si la fonctionnalité est intégrée correctement.  
  
 Pour vérifier l'accès aux données PowerPivot sur le serveur, procédez comme suit :  
  
1.  [Téléchargez](http://go.microsoft.com/fwlink/?LinkID=219108) l'exemple de données Picnic qui accompagne un didacticiel Reporting Services. Vous allez utiliser l'exemple de classeur des fichiers téléchargés pour vérifier l'accès aux données PowerPivot. Extrayez les fichiers.  
  
2.  Téléchargez un classeur PowerPivot dans la Bibliothèque PowerPivot ou une autre bibliothèque SharePoint.  
  
3.  Cliquez sur le document pour l'ouvrir à partir de la bibliothèque.  
  
4.  Cliquez sur un segment ou filtrez les données pour démarrer une requête PowerPivot. Le serveur charge les données PowerPivot en arrière-plan et renvoie les résultats. À l'étape suivante, vous allez vous connecter au serveur pour vérifier que les données sont chargées et mises en cache.  
  
5.  Démarrez SQL Server Management Studio à partir du groupe de programmes Microsoft SQL Server 2008 R2 dans le menu Démarrer. Si cet outil n'est pas installé sur votre serveur, vous pouvez passer à la dernière étape pour confirmer la présence de fichiers mis en cache.  
  
6.  Dans Type de serveur, sélectionnez **Analysis Services**.  
  
7.  Nom du serveur, entrez  **\<nom-serveur > \powerpivot**, où  **\<nom-serveur >** est le nom de l’ordinateur qui a l’installation de PowerPivot pour SharePoint.  
  
8.  Cliquez sur **Se connecter**.  
  
9. Dans l’Explorateur d’objets, cliquez sur **bases de données** pour afficher la liste des fichiers de données PowerPivot qui sont chargés.  
  
10. Sur le système de fichiers de l'ordinateur, vérifiez le dossier suivant pour déterminer si les fichiers sont mis en cache sur disque. La présence de fichiers mis en cache est une vérification supplémentaire que votre déploiement est opérationnel. Pour consulter le cache des fichiers, accédez au dossier \Program Files\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup.  
  
##  <a name="nextsteps"></a> Étapes de post-installation  
 Après avoir vérifié l'installation, terminez la configuration du service en créant une Galerie PowerPivot ou en ajustant certains paramètres de configuration. Pour exploiter au mieux les composants serveur que vous venez d'installer, vous pouvez télécharger [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] pour créer puis publier votre premier classeur PowerPivot.  
  
####  <a name="bkmk_disk"></a> Définir des limites supérieures sur l’utilisation de l’espace disque  
 Vous pouvez définir une limite maximale sur la quantité d'espace disque utilisée pour les fichiers de données PowerPivot qui sont mis en cache sur disque. L'option par défaut consiste à utiliser tout l'espace disque disponible. Pour obtenir des instructions sur la façon de limiter l’utilisation de l’espace disque, consultez [utilisation de l’espace disque configurer &#40;PowerPivot pour SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md).  
  
####  <a name="Upload"></a> Augmenter la taille maximale de téléchargement de fichiers pour les Applications Web SharePoint  
 Étant donné que les classeurs PowerPivot peuvent être volumineux, vous pouvez augmenter la taille maximale de téléchargement de fichier. Il y a deux paramètres de taille de fichier à configurer : Taille maximale du téléchargement pour l'application Web, et Taille maximale du classeur dans Excel Services. La taille de fichier maximale définie doit avoir la même valeur dans les deux applications. Pour obtenir des instructions, consultez [configurer une taille de téléchargement de fichier maximale &#40;PowerPivot pour SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
#### <a name="grant-sharepoint-permissions-to-workbook-users"></a>Accorder des autorisations SharePoint aux utilisateurs des classeurs  
 Les utilisateurs ont besoin d'autorisations SharePoint pour pouvoir publier ou consulter des classeurs. Veillez à accorder **vue** autorisations aux utilisateurs qui doivent consulter des classeurs publiés et **Contribute** autorisations aux utilisateurs qui publient ou gèrent des classeurs. Vous devez être administrateur de collection de sites pour pouvoir accorder des autorisations.  
  
1.  Dans le site, cliquez sur **Actions du Site**.  
  
2.  Cliquez sur **autorisations du Site**.  
  
3.  Activez la case à cocher pour la collection de sites **membres** groupe.  
  
4.  Dans le ruban, cliquez sur **accorder des autorisations**.  
  
5.  Entrez l'utilisateur de domaine Windows ou les comptes de groupe qui doivent avoir l'autorisation d'ajouter ou de supprimer des documents.  
  
6.  Cliquez sur **OK**.  
  
7.  Activez la case à cocher pour la collection de sites **visiteurs** groupe.  
  
8.  Dans le ruban, cliquez sur **accorder des autorisations**.  
  
9. Entrez l'utilisateur de domaine Windows ou les comptes de groupe qui doivent avoir l'autorisation de consulter des documents. Comme précédemment, n'utilisez pas d'adresses de messagerie ni de groupe de distribution si l'application est configurée pour une authentification classique.  
  
10. Cliquez sur **OK**.  
  
#### <a name="install-adonet-data-services-35-sp1"></a>Installer ADO.NET Data Services 3.5 SP1  
 ADO.NET Data Services est requis pour une exportation de flux de données de listes SharePoint. SharePoint 2010 n'inclut pas ce composant dans le programme PrerequisiteInstaller requis pour SharePoint. Par conséquent, vous devez l'installer manuellement. Pour plus d’informations sur la façon d’installer ADO.NET Data Services, consultez [installer ADO.NET Data Services pour prendre en charge les données exportations de flux des listes SharePoint](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
#### <a name="install-data-providers-used-in-data-refresh-and-check-user-permissions"></a>Installer les fournisseurs de données utilisés dans l'actualisation des données et vérifier les autorisations utilisateur  
 L'actualisation des données côté serveur autorise des utilisateurs à ré-importer des données mises à jour en mode sans assistance. Pour que l'actualisation des données réussisse, le serveur doit avoir le même fournisseur de données que celui utilisé à l'origine pour importer les données. De plus, le compte d'utilisateur sous lequel l'actualisation des données s'exécute requiert souvent des autorisations de lecture sur les sources de données externes. Veillez à vérifier les configurations requises pour l'activation et la configuration de l'actualisation des données afin de garantir le résultat. Pour plus d’informations, consultez [d’actualisation des données PowerPivot avec SharePoint 2010](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md).  
  
#### <a name="create-a-powerpivot-gallery"></a>Créer une bibliothèque Galerie PowerPivot  
 La bibliothèque Galerie PowerPivot est une bibliothèque qui inclut des options d'aperçu et de présentation pour consulter des classeurs PowerPivot sur un site SharePoint. L'utilisation de la bibliothèque Galerie PowerPivot pour publier et afficher des classeurs PowerPivot est recommandée pour sa fonction d'aperçu. De plus, si vous avez également déployé Reporting Services sur le même serveur SharePoint, une bibliothèque Galerie PowerPivot facilite la création de rapports. Vous pouvez lancer le Générateur de rapports à partir d'une bibliothèque Galerie PowerPivot pour baser un nouveau rapport sur un classeur PowerPivot publié. Pour plus d’informations sur la création et à l’aide de la bibliothèque, consultez [créer et personnaliser la galerie PowerPivot](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md) et [utiliser la galerie PowerPivot](../../analysis-services/power-pivot-sharepoint/use-power-pivot-gallery.md).  
  
#### <a name="tune-configuration-settings"></a>Régler les paramètres de configuration.  
 Une application de service PowerPivot est créée à l'aide des propriétés et des valeurs par défaut. Vous pouvez modifier les paramètres de configuration d'applications de service individuelles, pour modifier la méthodologie d'allocation des requêtes, définir des délais d'attente de serveur, modifier les seuils des événements de rapport des réponses aux requêtes ou spécifier la durée de conservation des données d'utilisation. Pour plus d’informations sur la configuration dans l’Administration centrale ou sur l’utilisation des fonctionnalités PowerPivot dans les applications SharePoint Web, consultez [d’Administration de serveur PowerPivot et de Configuration dans l’Administration centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473)   
 [Installer PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)   
 [Liste de vérification de déploiement : Montée en puissance en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)  
  
  
