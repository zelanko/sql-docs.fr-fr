---
title: Installation PowerPivot pour SharePoint 2013 | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
caps.latest.revision: 28
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: ef3e20cee4efd786e111a3c5a3e0f4864875e861
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152447"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a>PowerPivot for SharePoint 2013 Installation
  Les procédures décrites dans cette rubrique vous guident dans une installation d’un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] serveur en mode de déploiement de SharePoint. Ces étapes comprennent l'exécution de l'Assistant Installation de SQL Server ainsi que des tâches de configuration qui utilisent l'Administration centrale de SharePoint 2013.  
  
 **[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201  
  
 **Dans cette rubrique :**  
  
 [Arrière-plan](#bkmk_background)  
  
 [Conditions préalables](#bkmk_prereq)  
  
 [Étape 1 : Installer PowerPivot pour SharePoint](#InstallSQL)  
  
 [Étape 2 : configurer l'intégration SharePoint de base pour Analysis Services](#bkmk_config)  
  
 [Étape 3 : vérifier l'intégration](#bkmk_verify)  
  
 [Configurer le pare-feu Windows pour autoriser l'accès à Analysis Services](#bkmk_firewall)  
  
 [Mettre à niveau les classeurs et l'actualisation planifiée des données](#bkmk_upgrade_workbook)  
  
 [Au-delà de l’Installation de serveur unique-PowerPivot pour Microsoft SharePoint](#bkmk_multiple_servers)  
  
##  <a name="bkmk_background"></a> Arrière-plan  
 PowerPivot pour SharePoint est une collection de services de couche intermédiaire et de services principaux qui fournissent l'accès aux données PowerPivot dans une batterie de serveurs SharePoint 2013.  
  
-   **Services principaux :** si vous utilisez PowerPivot pour Excel pour créer des classeurs qui contiennent des données analytiques, vous devez disposer de PowerPivot pour SharePoint pour accéder à ces données dans un environnement serveur. Vous pouvez exécuter le programme d'installation de SQL Server sur un ordinateur qui possède un serveur SharePoint 2013 installé, ou sur un autre ordinateur sans logiciel SharePoint. Analysis Services n'a pas de dépendances de SharePoint.  
  
     **Remarque :** cette rubrique décrit l'installation du serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et les services principaux.  
  
-   **Niveau intermédiaire :** les améliorations apportées aux expériences PowerPivot dans SharePoint, dont la Galerie PowerPivot, l'actualisation planifiée des données, le tableau de bord de gestion et les fournisseurs de données. Pour plus d'informations sur l'installation et la configuration du niveau intermédiaire, consultez :  
  
    -   [Installer ou désinstaller PowerPivot pour SharePoint-complément &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
    -   [Configurer PowerPivot et déployer des Solutions &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
##  <a name="bkmk_prereq"></a> Conditions préalables  
  
1.  Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
2.  SharePoint Server 2013 Enterprise Edition est requis pour PowerPivot pour SharePoint. Vous pouvez également utiliser l'édition Enterprise Evaluation.  
  
3.  L'ordinateur doit être membre d'un domaine dans la même forêt Active Directory qu'Excel Services.  
  
4.  Le nom de l'instance PowerPivot doit être disponible. Vous ne pouvez pas avoir une instance nommée existante PowerPivot sur l'ordinateur d'installation d'Analysis Services en mode SharePoint.  
  
5.  Révision [matérielle et logicielle requise pour le serveur Analysis Services en Mode SharePoint &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).  
  
6.  Passez en revue les notes de version à [SQL Server 2012 Service Pack 1 Release Notes](http://go.microsoft.com/fwlink/?LinkID=248389) (http://go.microsoft.com/fwlink/?LinkID=248389).  
  
###  <a name="bkmk_sqleditions"></a> Configuration requise de SQL Server  
 Les fonctionnalités de Business Intelligence ne sont pas toutes disponibles dans toutes les éditions de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2012 (http://go.microsoft.com/fwlink/?linkid=232473) ](http://go.microsoft.com/fwlink/?linkid=232473) et [éditions et composants de SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
 Consultez les notes de publication [SQL Server 2012 SP1 Release Notes](ttp://go.microsoft.com/fwlink/?LinkID=248389) (http://go.microsoft.com/fwlink/?LinkID=248389).  
  
 [Notes de mise à jour de Microsoft SQL Server 2012 (http://go.microsoft.com/fwlink/?LinkId=236893)](http://go.microsoft.com/fwlink/?LinkId=236893).  
  
##  <a name="InstallSQL"></a> Étape 1 : Installer PowerPivot pour SharePoint  
 Au cours de cette étape, vous allez exécuter le programme d'installation de SQL Server pour installer un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint. Dans une étape suivante, vous allez configurer Excel Services pour utiliser ce serveur pour les modèles de données du classeur.  
  
1.  Exécutez l'Assistant Installation de SQL Server (Setup.exe).  
  
2.  Cliquez sur **Installation** dans le volet de navigation gauche.  
  
3.  Cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
4.  Si la page **Clé de produit** s'affiche, indiquez l'édition d'évaluation ou entrez une clé de produit pour une copie sous licence de l'édition entreprise. Cliquez sur **Suivant**. Pour plus d’informations sur les éditions, consultez [éditions et composants de SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).  
  
5.  Lisez et acceptez les termes du contrat de licence logiciel Microsoft, puis cliquez sur **Suivant**.  
  
6.  Si la page **Règles globales** s'affiche, passez en revue les informations sur les règles de l'Assistant Installation.  
  
7.  Dans la page **Microsoft Update** , il est recommandé d'utiliser Microsoft Update pour vérifier les mises à jour, puis de cliquer sur **Suivant**.  
  
8.  La page **Installer les fichiers d'installation** s'exécute pendant plusieurs minutes. Vérifiez les avertissements de règle ou les échecs de règle, puis cliquez sur **Suivant**.  
  
9. Si une autre page **Règles de support du programme d'installation**s'affiche, examinez les avertissements, puis cliquez sur **Suivant**.  
  
     **Remarque :** le Pare-feu Windows étant activé, un avertissement s'affiche indiquant qu'il faut ouvrir les ports pour activer l'accès à distance.  
  
10. Dans la page **Rôle d'installation** , sélectionnez **SQL Server PowerPivot pour SharePoint**. Cette option installe Analysis Services en mode SharePoint.  
  
     Éventuellement, vous pouvez ajouter une instance du moteur de base de données à votre installation. C'est une possibilité si vous installez une nouvelle batterie de serveurs et que vous avez besoin qu'un serveur de base de données exécute la configuration de la batterie et les bases de données de contenu. Cette option installe également [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
     Si vous ajoutez le moteur de base de données, il est installé en tant qu'instance nommée **PowerPivot** . Chaque fois que vous spécifiez une connexion à cette instance, entrez le nom de la base de données dans ce format : [`servername`] \PowerPivot.  
  
     Cliquez sur **Suivant**.  
  
     ![Le programme d’installation de rôle](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "rôle d’installation")  
  
11. Dans Sélection de fonctionnalités, une liste en lecture seule des fonctionnalités est affichée à titre d'information. Vous ne pouvez pas ajouter ou supprimer les éléments présélectionnés pour ce rôle. Cliquez sur **Suivant**.  
  
12. Dans la page **Configuration de l'instance** , un nom d'instance en lecture seule de PowerPivot est affiché à titre d'information. Ce nom d'instance est obligatoire et ne peut pas être modifié. Toutefois, vous pouvez entrer un ID d'instance unique pour spécifier un nom de répertoire descriptif et des clés de Registre. Cliquez sur **Suivant**.  
  
13. Dans la page **Configuration du serveur** , configurez tous les services pour le **Type de démarrage**automatique. Spécifiez le compte de domaine et le mot de passe de votre choix pour **SQL Server Analysis Services**, **(1)** dans le diagramme suivant.  
  
    -   Pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vous pouvez utiliser un compte d' **utilisateur de domaine** ou le compte **NetworkService** . N'utilisez pas de compte LocalSystem ou LocalService.  
  
    -   Si vous avez ajouté le Moteur de base de données SQL Server et l'Agent SQL Server, vous pouvez configurer les services à exécuter sous des comptes d'utilisateur de domaine ou sous un compte virtuel par défaut.  
  
    -   Ne configurez jamais de comptes de service avec votre propre compte d'utilisateur de domaine. Cela aurait pour conséquence d'accorder aux ressources du réseau les mêmes autorisations que celles dont vous bénéficiez. Si un utilisateur malveillant compromet le serveur, cet utilisateur est connecté avec vos informations d'identification de domaine. L'utilisateur dispose des autorisations pour télécharger ou utiliser les mêmes données et applications que vous.  
  
     Cliquez sur **Suivant**.  
  
     ![Configuration de serveur SSAS](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "Configuration de serveur SSAS")  
  
14. Si vous installez le [!INCLUDE[ssDE](../../../includes/ssde-md.md)], la page **Configuration du moteur de base de données** s'affiche. Dans [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Configuration, cliquez sur **ajouter l’utilisateur actuel** pour accorder des autorisations d’administrateur de compte sur l’instance du moteur de base de données de votre utilisateur.  
  
     Cliquez sur **Suivant**.  
  
15. Dans la page **Configuration d'Analysis Services** , cliquez sur **Ajouter l'utilisateur actuel** pour accorder vos autorisations administratives au compte d'utilisateur. Vous devrez avoir des autorisations d'administrateur pour configurer le serveur une fois l'installation terminée.  
  
    -   Dans la même page, ajoutez le compte d'utilisateur Windows de toute personne qui a aussi besoin d'autorisations d'administration. Par exemple, tout utilisateur qui souhaite se connecter à l'instance du [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , pour résoudre des problèmes de connexion de base de données ou obtenir des informations sur la version, doit avoir des autorisations d'administrateur système sur le serveur. Ajoutez le compte d'utilisateur de toute personne susceptible de devoir dépanner ou administrer le serveur.  
  
    -   > [!NOTE]  
        >  Les applications de service qui nécessitent l'accès à l'instance de serveur Analysis Services doivent avoir des autorisations d'administration Analysis Services. Par exemple, ajoutez les comptes de service pour Excel Services, Power View et les services Performance Point. En outre, ajoutez le compte de batterie de serveurs SharePoint, utilisé comme identité de l'application Web qui héberge l'Administration centrale.  
  
     Cliquez sur **Suivant**.  
  
16. Dans la page **Rapport d'erreurs** , cliquez sur **Suivant**.  
  
17. Dans la page **Prêt pour l'installation** , cliquez sur **Installer**.  
  
18. Si vous voyez la boîte de dialogue **Redémarrage requis de l'ordinateur**, cliquez sur **OK**.  
  
19. Lorsque l'installation est terminée, cliquez sur **Fermer**.  
  
20. Redémarrez l'ordinateur.  
  
21. Si vous avez un pare-feu dans votre environnement, consultez la rubrique de la documentation en ligne de SQL Server [configurer le pare-feu Windows pour autoriser l’accès à Analysis Services](../configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
### <a name="verify-the-sql-server-installation"></a>Vérifier l'installation de SQL Server  
 Vérifiez que le service Analysis Services est en cours d'exécution.  
  
1.  Dans Microsoft Windows, cliquez sur **Démarrer**, sur **Tous les programmes**, puis cliquez sur le groupe **Microsoft SQL Server 2012** .  
  
2.  Cliquez sur **SQL Server Management Studio**.  
  
3.  Connectez-vous à l'instance Analysis Services, par exemple **[nom serveur]\POWERPIVOT**. Si vous vous connectez à l'instance, vous avez vérifié que le service s'exécute.  
  
##  <a name="bkmk_config"></a> Étape 2 : configurer l'intégration SharePoint de base pour Analysis Services  
 Les étapes suivantes décrivent les modifications de configuration nécessaires pour que vous puissiez interagir avec des modèles de données avancés Excel dans une bibliothèque de documents SharePoint. Effectuez ces étapes, une fois que vous avez installé SharePoint Server 2013 et SQL Server Analysis Services.  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a>Accorder des droits d'administration de serveur Excel Services dans Analysis Services  
 Vous n'avez pas besoin de terminer cette section si lors de l'installation d'Analysis Services, vous avez ajouté le compte de service de l'application Excel Services en tant qu'administrateur Analysis Services.  
  
1.  Sur le serveur Analysis Services, démarrez SQL Server Management Studio et connectez-vous à l'instance Analysis Services, par exemple `[MyServer]\POWERPIVOT`.  
  
2.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur le nom de l'instance, puis cliquez sur **Propriétés**.  
  
     ![Afficher les propriétés d’un serveur SSAS](../../../sql-server/install/media/as-ssms-proeprties.gif "afficher les propriétés d’un serveur SSAS")  
  
3.  Dans le volet gauche, cliquez sur **Sécurité**. Ajoutez la connexion de domaine que vous avez configurée pour l'application Excel Services à l'étape 1.  
  
     ![Paramètres de sécurité d’un serveur SSAS](../../../sql-server/install/media/as-ssms-security.gif "des paramètres de sécurité d’un serveur SSAS")  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a>Configurer Excel Services pour l'intégration d'Analysis Services  
  
1.  Dans l'Administration centrale de SharePoint, sous le groupe Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de votre application de service, par défaut **Application Excel Services**.  
  
3.  Dans la page **Gérer l'application Excel Services**, cliquez sur **Paramètres du modèle de données**.  
  
4.  Cliquez sur **Ajouter un serveur**.  
  
5.  Dans **Nom du serveur**, tapez le nom du serveur Analysis Services et le nom de l'instance PowerPivot. Par exemple, `MyServer\POWERPIVOT`. Le nom de l'instance PowerPivot est obligatoire.  
  
     Tapez une description.  
  
6.  Cliquez sur **OK**.  
  
7.  Les modifications prendront effet après quelques minutes ou vous pouvez **Arrêter** et **Démarrer** le service **Services de calcul Excel**. Pour  
  
     Une autre option consiste à ouvrir une invite de commandes avec des privilèges d'administrateur, puis taper `iisreset /noforce`.  
  
     Vérifiez que le serveur est reconnu par Excel Services en examinant les entrées du journal ULS. Les entrées ressemblent à l'exemple suivant :  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="bkmk_verify"></a> Étape 3 : vérifier l'intégration  
 Les étapes suivantes vous guident tout au long des processus de création et de téléchargement d'un classeur pour vérifier l'intégration d'Analysis Services. Vous aurez besoin d'une base de données SQL Server pour terminer les étapes.  
  
1.  **Remarque :** si vous disposez déjà d'un classeur avancé avec des segments ou des filtres, téléchargez-le dans votre bibliothèque de documents SharePoint et vérifiez que vous pouvez interagir avec les segments et les filtres à partir de la vue de la bibliothèque de documents.  
  
2.  Démarrez un nouveau classeur dans Excel.  
  
3.  Sous l'onglet Données, cliquez sur **À partir d'autres sources** sur le ruban dans le groupe **Obtenir des données externes**.  
  
4.  Sélectionnez **À partir de SQL Server**.  
  
5.  Dans l' **Assistant Connexion de données**, entrez le nom de l'instance SQL Server qui contient la base de données à utiliser.  
  
6.  ou dans Références de connexion, vérifiez que l'option **Utiliser l'authentification Windows** est sélectionnée, puis cliquez sur **Suivant**.  
  
7.  Sélectionnez la base de données à utiliser.  
  
8.  Assurez-vous que la case à cocher **Connexion à une table spécifique** est activée.  
  
9. Activez la case à cocher **Activer la sélection de plusieurs tables et ajouter des tables au modèle de données Excel** .  
  
10. Sélectionnez les tables à importer.  
  
11. Activez la case à cocher **Importer les relations entre les tables sélectionnées**, puis cliquez sur **Suivant**. Importer plusieurs tables d'une base de données relationnelle vous permet de travailler avec les tables qui sont déjà associées. Vous réduisez le nombre d'étapes nécessaires, car vous n'avez pas à créer les relations manuellement.  
  
12. Dans la page **Enregistrement du fichier de connexion de données et fin** de l'Assistant, entrez un nom pour votre connexion et cliquez sur **Terminer**.  
  
13. La boîte de dialogue **Importer les données** s'affiche. Choisissez **Rapport de tableau croisé dynamique**, puis cliquez sur **OK**.  
  
14. Une liste de champs de tableau croisé dynamique s'affiche dans le classeur.   
    Dans la liste de champs, cliquez sur l'onglet **Tous** .  
  
15. Ajoutez des champs aux zones Ligne, Colonnes et Valeur de la liste de champs.  
  
16. Ajoutez un segment ou un filtre au tableau croisé dynamique. **N'ignorez pas cette étape**. Un segment ou un filtre est l'élément qui vous permet de vérifier votre installation d'Analysis Services.  
  
17. Enregistrez le classeur dans une bibliothèque de documents sur un serveur SharePoint 2013 sur lequel Excel Services est configuré. Vous pouvez également enregistrer le classeur sur un partage de fichiers et le télécharger dans la bibliothèque de documents SharePoint Server 2013.  
  
18. Cliquez sur le nom de votre classeur pour l'afficher dans SharePoint et cliquez sur le segment ou modifier le filtre que vous avez ajouté précédemment. Si une mise à jour de données se produit, vous savez qu'Analysis Services est installé et disponible dans Excel Services. Si vous ouvrez le classeur dans Excel vous utiliserez une copie mise en cache et non pas le serveur Analysis Services.  
  
##  <a name="bkmk_firewall"></a> Configurer le pare-feu Windows pour autoriser l'accès à Analysis Services  
 Utilisez les informations de la rubrique [configurer le pare-feu Windows pour autoriser l’accès à Analysis Services](../configure-the-windows-firewall-to-allow-analysis-services-access.md) pour déterminer si vous devez débloquer des ports dans un pare-feu pour autoriser l’accès à Analysis Services ou PowerPivot pour SharePoint. Vous pouvez suivre les étapes fournies dans la rubrique pour configurer les paramètres des ports et du pare-feu. Dans la pratique, il est conseillé d'effectuer ces étapes en même temps pour permettre l'accès à votre serveur Analysis Services.  
  
##  <a name="bkmk_upgrade_workbook"></a> Mettre à niveau les classeurs et l'actualisation planifiée des données  
 Les étapes nécessaires à la mise à niveau des classeurs créés dans les versions antérieures de PowerPivot dépendent de la version de PowerPivot dans laquelle le classeur a été créé. Pour plus d’informations, consultez [Mettre à niveau les classeurs et l’actualisation planifiée des données &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_multiple_servers"></a> Au-delà de l’Installation de serveur unique-PowerPivot pour Microsoft SharePoint  
 **Serveur Web frontal (WFE)** ou **intermédiaire :**: À utiliser un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] serveur en mode SharePoint dans une batterie de serveurs SharePoint plu et installer des fonctionnalités PowerPivot supplémentaires dans la batterie de serveurs, exécutez le package de programme d’installation **spPowerPivot.msi** sur chacun des serveurs SharePoint. Le fichier spPowerPivot.msi installe les fournisseurs de données requis et l'outil de configuration PowerPivot pour SharePoint 2013.  
  
 Pour plus d'informations sur l'installation et la configuration du niveau intermédiaire, consultez :  
  
-   [Installer ou désinstaller PowerPivot pour SharePoint-complément &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   Pour télécharger le fichier .msi, consultez [Microsoft SQL Server 2014 PowerPivot pour Microsoft SharePoint 2013](http://go.microsoft.com/fwlink/?LinkID=324854).  
  
-   [Configurer PowerPivot et déployer des Solutions &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
 **Redondance et charge du serveur :** installation d’une seconde ou plus [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] serveurs en mode SharePoint fournit la redondance de le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fonctionnalités du serveur. Les serveurs supplémentaires distribuent également la charge entre plusieurs serveurs. Pour plus d'informations, consultez les documents suivants :  
  
-   [Configurer Analysis Services pour le traitement des modèles de données dans Excel Services](http://technet.microsoft.com/library/jj614437\(v=office.15\)) (http://technet.microsoft.com/library/jj614437(v=office.15)).  
  
-   [Gérer les paramètres de modèle de données Excel Services (SharePoint Server 2013)](http://technet.microsoft.com/library/jj219780\(v=office.15\)) (http://technet.microsoft.com/library/jj219780(v=office.15)).  
  
 ![Les paramètres SharePoint](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "paramètres SharePoint") [envoyer les informations de contact et les commentaires via Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Voir aussi  
 [Migrer PowerPivot vers SharePoint 2013](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Installer ou désinstaller PowerPivot pour SharePoint-complément &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [Mettre à niveau les classeurs et l’actualisation planifiée des données &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  