---
title: Installer Reporting Services mode SharePoint pour SharePoint 2013 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1a249c7a6fa260d5800c81b33b7674a2affa4eb5
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952225"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a>Installer le mode SharePoint de Reporting Services pour SharePoint 2013
  Les procédures de cette rubrique constituent un guide d'installation sur un serveur unique de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Ces étapes comprennent l'exécution de l'Assistant Installation de SQL Server ainsi que des tâches de configuration qui utilisent l'Administration centrale de SharePoint. La rubrique peut également être utilisée pour des procédures individuelles dans le cadre de la mise à jour d'une installation existante, par exemple, pour créer une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  Remarque sur &#124; SharePoint 2013 **:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le mode SharePoint ne prend **pas** en charge l’architecture mutualisée de SharePoint Server.|  
  
 Pour plus d'informations sur l'ajout de serveurs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supplémentaires à une batterie de serveurs existante, consultez les rubriques suivantes :  
  
-   [Ajouter un serveur de rapports supplémentaire à une batterie &#40;montée en puissance SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [Ajouter un serveur Web frontal Reporting Services supplémentaire à un pool](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 Une installation sur un serveur unique est utile pour les scénarios de développement et de tests, mais n'est pas recommandée pour les environnements de production.  
  
 **Dans cette rubrique :**  
  
-   [Exemple de déploiement sur un serveur unique](#bkmk_singleserver)  
  
-   [Comptes d’installation](#bkmk_setupaccounts)  
  
-   [Étape 1 : Installer Reporting Services serveur de rapports en mode SharePoint @ no__t-0  
  
-   [Étape 2 : Inscrire et démarrer le service Reporting Services SharePoint @ no__t-0  
  
-   [Étape 3 : Créer une application de service Reporting Services @ no__t-0  
  
-   [Étape 4 : Activez la fonctionnalité de collection de sites Power View. ](#bkmk_powerview)  
  
-   [Script Windows PowerShell pour les étapes 1-4](#bkmk_full_script)  
  
-   [Additional Configuration](#bkmk_additional_config) , dont la configuration d'abonnements et d'alertes, les types de contenu [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et d'Excel Services pour utiliser un serveur Analysis Services.  
  
-   [Vérifier l’installation](#bkmk_verify_installation)  
  
##  <a name="bkmk_singleserver"></a> Exemple de déploiement sur un serveur unique  
 Une installation sur un serveur unique est utile pour les scénarios de développement et de tests, mais n'est pas recommandée pour un environnement de production. Un environnement à serveur unique fait référence à un seul ordinateur sur lequel SharePoint et les composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont installés. La rubrique ne couvre pas la montée en puissance parallèle avec plusieurs serveurs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Le diagramme suivant montre les composants qui font partie d'un déploiement d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un seul serveur.  
  
|||  
|-|-|  
|**(1)**|Service SharePoint installé à partir d'une installation SQL Server. Vous pouvez créer une ou plusieurs applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|**(2)**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le complément pour les produits SharePoint fournit les composants d’interface utilisateur sur les serveurs SharePoint.|  
|**(3)**|L'application Excel Services est utilisée par Power View et PowerPivot.|  
|**(4)**|Application de service PowerPivot.|  
  
 ![Déploiement de SSRS en mode SharePoint sur un serveur unique](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "Déploiement de SSRS en mode SharePoint sur un serveur unique")  
  
> [!TIP]  
>  Pour obtenir des exemples de déploiement plus complexes, consultez [Topologies de déploiement pour les fonctionnalités SQL Server BI dans SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).  
  
##  <a name="bkmk_setupaccounts"></a> Comptes d'installation  
 Cette section décrit les comptes et les autorisations utilisés pour les étapes de déploiement principales de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.  
  
 **Installation et inscription du service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :**  
  
-   Le compte actuel au cours de l’installation (appelé « compte d’installation ») de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint doit disposer des droits d’administration sur l’ordinateur local. Si vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] après l’installation de SharePoint et que le compte d’installation est également membre du groupe administrateurs de batterie de serveurs SharePoint, l’installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inscrira le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour vous. Si vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avant l’installation de SharePoint ou si le compte d’installation n’est pas membre du groupe administrateurs de batterie, vous inscrivez le service manuellement. Consultez la section [Step 2 : Inscrivez-vous et démarrez le Reporting Services SharePoint service @ no__t-0.  
  
 **Création d'applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  
  
-   Après avoir installé et inscrit le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , créez une ou plusieurs applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le « compte de service de la batterie de serveurs SharePoint » doit être temporairement membre du groupe des administrateurs locaux pour permettre la création de l’application de service Reporting Services. Pour plus d’informations sur les autorisations de compte SharePoint 2013, consultez [autorisations de compte et paramètres de sécurité dans sharepoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).  
  
     Pour des raisons de sécurité, il est recommandé que les comptes d'administrateur de la batterie de serveurs SharePoint ne soient pas également des comptes d'administrateurs locaux du système d'exploitation. Si vous ajoutez un compte d'administrateur de batterie de serveurs au groupe des administrateurs locaux dans le cadre du processus d'installation, nous vous recommandons de supprimer le compte du groupe des administrateurs locaux une fois l'installation terminée.  
  
##  <a name="bkmk_install_SSRS"></a> Étape 1 : Installer Reporting Services serveur de rapports en mode SharePoint  
 Cette étape installe un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint et le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint. En fonction des éléments déjà installés sur votre ordinateur, il est possible que certaines pages d'installation décrites dans les étapes suivantes ne s'affichent pas.  
  
1.  Exécutez l'Assistant Installation de SQL Server (Setup.exe).  
  
2.  Cliquez sur **Installation** dans la partie gauche de l'Assistant, puis cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
3.  Cliquez sur **OK** dans la page **Règles de support du programme d'installation** , si toutes les règles sont passées.  
  
4.  Cliquez sur **Installer** dans la page **Fichiers de support du programme d'installation** . En fonction des éléments déjà installés sur votre ordinateur, le message suivant peut s'afficher :  
  
    -   « Un ou plusieurs des fichiers affectés ont des opérations en attente. Vous devez redémarrer votre ordinateur une fois le processus d’installation terminé. »  
  
    -   Cliquez sur **OK**.  
  
5.  Cliquez sur **Suivant** lorsque les fichiers de support sont installés et que les pages **Règles de support** affichent l'état **Réussite**. Examinez tout avertissement ou problème bloquant.  
  
6.  Dans la page **Type d'installation** , cliquez sur **Ajouter des fonctionnalités à une instance existante de SQL Server 2014**. Sélectionnez l'instance appropriée dans la liste déroulante et cliquez sur **Suivant**.  
  
7.  Si la page **Clé de produit** s’affiche, tapez votre clé ou acceptez la valeur par défaut de l’édition d’évaluation « Enterprise Evaluation ».  
  
     Cliquez sur **Suivant**.  
  
8.  Si la page Termes du contrat de licence s'affiche, lisez et acceptez les termes du contrat de licence. Microsoft vous remercie d'accepter d'envoyer des données d'utilisation des fonctionnalités dans le but d'améliorer ces fonctionnalités et la prise en charge.  
  
     Cliquez sur **Suivant**.  
  
9. Si la page **Rôle d'installation** s'affiche, sélectionnez **Installation de fonctionnalités SQL Server**.  
  
     Cliquez sur **Suivant**.  
  
     ![Installation des fonctionnalités SQL Server pour le rôle d’installation](../../../2014/sql-server/install/media/rs-setuprole.gif "Installation des fonctionnalités SQL Server pour le rôle d’installation")  
  
10. Sélectionnez ce qui suit dans la page **Sélection de fonctionnalités** :  
  
    -   **Reporting Services - SharePoint**  
  
    -   **Complément Reporting Services pour les produits SharePoint**  
  
         ![Remarque](../../../2014/reporting-services/media/rs-fyinote.png "Remarque") L’option de l’Assistant Installation pour installer le complément est une nouveauté de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] la version.  
  
    -   Si vous n'avez pas encore d'instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)]SQL Server, vous pouvez également sélectionner les **Services de moteur de base de données** et les **Outils de gestion - Complet** pour un environnement complet.  
  
     Cliquez sur **Suivant**.  
  
     ![Sélection de fonctionnalités SSRS pour le mode SharePoint](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "Sélection de fonctionnalités SSRS pour le mode SharePoint")  
  
11. Si la page **Règles d'installation** s'affiche. Examinez tout avertissement ou problème bloquant. Ensuite, cliquez sur **Suivant**.  
  
12. Si vous avez sélectionné les services de moteur de base de données, acceptez l'instance par défaut de **MSSQLSERVER** dans la page **Configuration de l'instance** et cliquez sur **Suivant**.  
  
     ![remarque](../../../2014/reporting-services/media/rs-fyinote.png "remarque")L’architecture de service SharePoint Reporting Services n’est pas basée sur une « instance » SQL Server comme l’était la précédente architecture de Reporting Services.  
  
13. Examinez la page **Espace disque nécessaire** et cliquez sur **Suivant**.  
  
14. Si la page **Configuration du serveur** s'affiche, entrez les informations d'identification appropriées. Si vous souhaitez utiliser les fonctionnalités de données d'alerte ou d'abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez modifier le **Type de démarrage** de SQL Server Agent en **automatique**. En fonction des éléments déjà installés sur votre ordinateur, la page **Configuration du serveur** peut ne pas s'afficher.  
  
     Cliquez sur **Suivant**.  
  
15. Si vous avez sélectionné les services de moteur de base de données, la page **Configuration du moteur de base de données** s'affiche où vous pouvez ajouter les comptes appropriés à la liste des administrateurs SQL puis cliquer sur **Suivant**.  
  
16. Dans la page **Configuration de Reporting Services** , l'option **Installer uniquement** devrait être sélectionnée. Cette option installe les fichiers du serveur de rapports mais ne configure pas l'environnement SharePoint pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    > [!NOTE]  
    >  Lorsque l'installation de SQL Server est terminée, suivez les sections suivantes de cette rubrique pour configurer l'environnement SharePoint. Cela inclut l'installation du service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et la création des applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     ![Assistant Installation de SQL Server-page Configuration de ssrs](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server Assistant installation-page Configuration de SSRS")  
  
17. Aidez Microsoft à améliorer les fonctionnalités et services de SQL Server en activant la case à cocher pour envoyer les rapports d'erreurs dans la page **Rapport d'erreurs** .  
  
     Cliquez sur **Suivant**.  
  
18. Examinez tout avertissement, puis cliquez sur **Suivant** dans la page **Règles de configuration de l'installation** .  
  
19. Dans la page **Prêt pour l'installation** , lisez le résumé d'installation, puis cliquez sur **Suivant**. Le résumé inclut un nœud enfant **Mode SharePoint Reporting Services** qui affiche la valeur **SharePointFilesOnlyMode**. Cliquez sur **Installer**.  
  
20. L'installation prend plusieurs minutes. Vous verrez la page **Terminé** avec les fonctionnalités répertoriées et l'état de chaque fonctionnalité. Une boîte de dialogue d'informations peut s'afficher indiquant que l'ordinateur doit être redémarré.  
  
##  <a name="bkmk_install_SSRS_sharedservice"></a> Étape 2 : Inscrire et démarrer le service Reporting Services SharePoint  
 ![Contenu relatif à PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "Contenu relatif à PowerShell")  
  
> [!NOTE]  
>  Si vous procédez à une installation dans une batterie de serveurs SharePoint existante, vous pouvez ignorer les étapes de cette section. Le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint est installé et démarré lors de l'exécution de l'Assistant Installation de SQL Server dans le cadre de la section précédente de ce document.  
  
 Voici les raisons habituelles pour lesquelles vous devez inscrire manuellement le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Vous avez installé le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avant d'installer SharePoint.  
  
-   Le compte utilisé pour l'installation du mode SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'était pas membre du groupe d'administrateurs de la batterie de serveurs SharePoint. Pour plus d'informations, consultez la section [Setup accounts](#bkmk_setupaccounts).  
  
 Les fichiers nécessaires ont été installés dans le cadre de l'assistant Installation de SQL Server, mais les services doivent être enregistrés dans la batterie de serveurs SharePoint. La version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] inclut la prise en charge de PowerShell pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.  
  
 Les étapes suivantes vous guident dans l'ouverture de SharePoint Management Shell et l'exécution des applets de commande :  
  
1.  Cliquez sur le bouton **Démarrer** .  
  
2.  Cliquez sur le groupe **Produits Microsoft SharePoint 2013** .  
  
3.  Cliquez avec le bouton droit sur **SharePoint 2013 Management Shell** , puis sélectionnez **Exécuter en tant qu'administrateur**. REMARQUE : les commandes SharePoint ne sont pas identifiées dans la fenêtre standard de Windows PowerShell. Utilisez **SharePoint 2013 Management Shell**.  
  
4.  Exécutez la commande PowerShell suivante pour installer le service SharePoint. Si la commande est correctement exécutée, une nouvelle ligne apparaît dans le shell de gestion. **Aucun message n'est retourné** au shell de gestion lorsque la commande est correctement exécutée :  
  
    ```  
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  Si un message d'erreur semblable au suivant s'affiche :  
    >   
    >  Install-SPRSService : Le terme « install-SPRSService » **n’est pas reconnu** en tant que  
    > nom d'applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez  
    > l'orthographe du nom, ou si un chemin d'accès existe, vérifiez que le chemin d'accès est  
    > correct et réessayez.  
  
5.  Exécutez la commande PowerShell suivante pour installer le proxy de service. Si la commande est correctement exécutée, une nouvelle ligne apparaît dans le shell de gestion. **Aucun message n'est retourné** au shell de gestion lorsque la commande est correctement exécutée :  
  
    ```  
    Install-SPRSServiceProxy  
    ```  
  
6.  Exécutez la commande PowerShell suivante pour démarrer le service ou reportez-vous aux notes suivantes pour accéder aux instructions sur le démarrage du service de l'Administration centrale de SharePoint :  
  
    ```  
    get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 Soit vous êtes dans Windows Powershell au lieu de SharePoint Management Shell, soit le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas installé. Pour plus d’informations sur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et PowerShell, consultez [Applets de commande PowerShell pour le mode SharePoint de Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
 Vous pouvez également démarrer le service depuis l'Administration centrale de SharePoint au lieu d'exécuter la troisième commande PowerShell. Les étapes suivantes sont également utiles pour vérifier que le service fonctionne.  
  
1.  Dans l'Administration centrale de SharePoint, cliquez sur **Gérer les services sur le serveur** dans le groupe **Paramètres système** .  
  
2.  Repérez le **service SQL Server Reporting Services** et cliquez sur **Démarrer** dans la colonne Action.  
  
3.  L'état du service Reporting Services passe d' **Arrêté** à **Démarré**. Si le service Reporting Services n'est pas dans la liste, installez-le à l'aide de PowerShell.  
  
    > [!NOTE]  
    >  Si le service Reporting Services reste à l’état **Démarrage** et ne passe pas à **Démarré**, vérifiez que le service « Administration SharePoint 2013 » est démarré dans le Gestionnaire de serveur Windows.  
  
##  <a name="bkmk_create_serrviceapplication"></a> Étape 3 : Créer une application de service Reporting Services  
 Cette section fournit les étapes pour créer une application de service et une description des propriétés, si vous consultez une application de service existante.  
  
1.  Dans l'Administration centrale de SharePoint, sous le groupe **Gestion des applications** , cliquez sur **Gérer les applications de service**.  
  
2.  Dans le ruban SharePoint, cliquez sur le bouton **Nouveau** .  
  
3.  Dans le menu Nouveau, cliquez sur **Application de service SQL Server Reporting Services**.  
  
    > [!IMPORTANT]  
    >  Si l’option [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne figure pas dans la liste, cela **indique que le service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n’est pas installé**. Examinez la section précédente sur l'utilisation des applets de commande PowerShell pour installer le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
4.  Dans la page **Créer une application de service SQL Server Reporting Services** , entrez un nom pour l'application. Si vous créez plusieurs applications de service Reporting Services, un nom descriptif ou une convention d'affectation de noms peut vous aider à organiser vos opérations d'administration et de gestion.  
  
5.  Dans la section **Pool d’applications** , créez un pool d’applications pour l’application (recommandé). Si vous utilisez le même nom pour le pool d'applications et l'application de service, cela peut simplifier l'administration actuelle. Ceci peut aussi être affecté par le nombre d'applications de service que vous allez créer et si vous devez en utiliser plusieurs dans un même pool d'applications. Consultez la documentation de SharePoint Server pour obtenir des recommandations et les meilleures pratiques pour la gestion du pool d'applications.  
  
     Sélectionnez ou créez un compte de sécurité pour le pool d'applications. Veillez à spécifier un compte d'utilisateur de domaine. Un compte d'utilisateur de domaine autorise l'utilisation de la fonctionnalité Compte géré de SharePoint, qui vous permet de mettre à jour des mots de passe et des informations sur le compte dans un seul emplacement. Des comptes de domaine sont requis si vous prévoyez une montée en puissance parallèle du déploiement incluant des instances de service supplémentaires qui s'exécuteront sous la même identité.  
  
6.  Dans le **Serveur de base de données**, utilisez le serveur actuel ou choisissez un autre serveur SQL Server.  
  
7.  Dans **Nom de la base de données** , la valeur par défaut est `ReportingService_<guid>`, qui est un nom de base de données unique. Si vous tapez une nouvelle valeur, tapez une valeur unique. Il s'agit de la nouvelle base de données créée spécifiquement pour une application de service.  
  
8.  Dans **Authentification de la base de données**, la valeur par défaut est Authentification Windows. Si vous choisissez **Authentification SQL**, reportez-vous à la documentation SharePoint pour les méthodes recommandées concernant l'utilisation de ce type d'authentification dans un déploiement SharePoint.  
  
9. Dans la section **Association d'application Web** , sélectionnez l'application Web à configurer pour l'accès de l'application de service Reporting Services actuelle. Vous pouvez associer une application de service Reporting Services à une application Web. Si toutes les applications Web actuelles sont déjà associées à une application de service Reporting Services, un message d'avertissement apparaît.  
  
10. Cliquez sur **OK**.  
  
11. Le processus de création d'une application de service peut durer plusieurs minutes. Lorsqu'il est terminé, vous voyez s'afficher un message de confirmation et un lien vers la page **Configurer les abonnements et les alertes** . Terminez l'étape de configuration si vous souhaitez utiliser les fonctionnalités d'abonnement et d'alerte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou la fonctionnalité d'alertes de données. Pour plus d’informations, consultez [Configurer les abonnements et les alertes pour les applications de service de SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
 ![](../../../2014/reporting-services/media/rs-powershellicon.jpg "Contenu relatif") à PowerShell contenu relatif à PowerShell pour plus d’informations sur l’utilisation de PowerShell pour créer une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez :  
  
-   Consultez la section suivante [Script Windows PowerShell pour les étapes 1 à 4](#bkmk_full_script).  
  
-   Rubrique [Pour créer une application de service Reporting Services à l’aide de PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).  
  
##  <a name="bkmk_powerview"></a> Étape 4 : Activez la fonctionnalité de collection de sites Power View.  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] est une fonctionnalité du complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint qui permet la collection de sites. Elle est activée automatiquement pour les collections de sites racine et celles créés après l'installation de la macro complémentaire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si vous envisagez d'utiliser [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], vous devez vérifier que la fonctionnalité est activée.  
  
 Si vous installez le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint après l'installation du produit SharePoint Server, la fonctionnalité d'intégration du serveur de rapports et la fonctionnalité d'intégration Power View sont uniquement activées pour les collections de sites racine. Pour les autres collections de sites, activez manuellement les fonctionnalités.  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a>Pour activer ou vérifier la fonctionnalité de collection de sites Power View  
  
1.  Les étapes suivantes impliquent que votre site SharePoint est configuré pour **version d'affichage**2013.  
  
     Ouvrez votre navigateur sur le site SharePoint souhaité. Par exemple, http://\<nom_serveur>/sites/bi  
  
2.  Cliquez sur **paramètres**![paramètres SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "paramètres SharePoint").  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Dans le groupe **Administration de la collection de sites** , cliquez sur **Fonctionnalités de la collection de sites**.  
  
5.  Recherchez **Fonctionnalité d'intégration de Power View** dans la liste.  
  
6.  Cliquez sur **Activer**. L'état de la fonctionnalité devient **Actif**.  
  
 Cette procédure doit être exécutée par collection de sites. Pour plus d'informations, consultez [Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).  
  
##  <a name="bkmk_full_script"></a>Script Windows PowerShell pour les étapes 1-4  
 Le script PowerShell de cette section correspond à l'exécution des étapes 1 à 4 des sections précédentes. Le script effectue les tâches suivantes :  
  
-   Installe le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et le proxy de service, puis démarre le service.  
  
-   Crée un proxy de service nommé « Reporting Services ».  
  
-   Crée une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nommée « application Reporting Services ».  
  
-   Active les fonctionnalités [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] pour une collection de sites.  
  
 Paramètres  
  
-   Mettez à jour le paramètre **-Account** du proxy de service. Le compte doit être un compte de service administré dans la batterie de serveurs SharePoint. Pour plus d'informations, consultez la rubrique SharePoint [Planification des comptes d’administration et de service dans SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).  
  
-   Mettez à jour le paramètre **-DatabaseServer** pour l’application de service. Ce paramètre représente l'instance du moteur de base de données.  
  
-   Mettez à jour le paramètre **-url** du site pour lequel vous souhaitez activer la fonctionnalité [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 **Pour utiliser le script :**  
  
1.  Ouvrez Windows PowerShell avec des privilèges d'administrateur.  
  
2.  Copiez le code suivant dans la fenêtre de script.  
  
3.  Mettez à jour les trois paramètres décrits dans la section précédente, puis exécutez le script.  
  
```  
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
write-host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
write-host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy  
  
```  
  
##  <a name="bkmk_additional_config"></a> Configuration supplémentaire  
 Cette section décrit les étapes de configuration supplémentaires qui sont importantes dans la plupart des déploiements de SharePoint.  
  
###  <a name="bkmk_configure_ECS"></a>Configurer Excel Services et PowerPivot  
 Si vous souhaitez afficher des rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View dans un classeur Excel 2013 dans SharePoint, une application Excel Services de la batterie de serveurs doit être configurée pour utiliser un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. De plus, le compte de sécurité du pool d'applications utilisé par l'application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doit être administrateur sur le serveur Analysis Services. Pour plus d'informations, consultez les documents suivants :  
  
-   La section « configurer Excel Services pour l’intégration de Analysis Services » dans [PowerPivot pour SharePoint installation de 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).  
  
-   [Gérer les paramètres de modèle de données Excel Services (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).  
  
###  <a name="bkmk_provision_agent"></a> Configurer les abonnements et les alertes  
 Les fonctionnalités d'abonnement et d'alerte de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent exiger la configuration des autorisations de SQL Server Agent. Si un message d'erreur apparaît indiquant que SQL Server Agent est obligatoire alors que vous avez vérifié qu'il s'exécute, mettez à jour les autorisations. Cliquez sur le lien **Configurer les abonnements et les alertes** dans la page de création réussie d'application de service pour accéder à une autre page dans laquelle vous pouvez configurer SQL Server Agent. L'étape de configuration est nécessaire si votre déploiement dépasse les limites des machines, par exemple lorsque l'instance de base de données SQL Server se trouve sur un autre ordinateur. Pour plus d’informations, consultez [Configurer les abonnements et les alertes pour les applications de service de SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a>Configurer la messagerie électronique pour les applications de service SSRS  
 La fonctionnalité d'alertes de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] envoie des alertes via des messages électroniques. Pour envoyer du courrier électronique, vous devrez peut-être configurer votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et modifier l'extension de remise par messagerie pour l'application de service. Si vous prévoyez d'utiliser l'extension de remise par messagerie pour la fonctionnalité d'abonnement d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , les paramètres de courrier électronique sont nécessaires. Pour plus d’informations, consultez [Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a>Ajouter les types de contenu Reporting Services aux bibliothèques de contenu  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit des types de contenu prédéfinis pour gérer les fichiers de sources de données partagées (.rsds), les modèles de rapports (.smdl) et les fichiers de définition de rapport (.rdl) du Générateur de rapports. L'ajout à une bibliothèque des types de contenu **Rapport du Générateur de rapports**, **Modèle de rapport**et **Source de données du rapport** active la commande **Nouveau** , qui permet de créer de nouveaux documents de ce type. Pour plus d’informations, consultez [Ajouter des types de contenu de serveur &#40;de rapports à une bibliothèque&#41;Reporting Services en mode intégré SharePoint](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
### <a name="activate-the-report-server-file-sync-feature"></a>Activer la fonctionnalité de synchronisation des fichiers de serveur de rapports  
 Si vos utilisateurs téléchargent fréquemment des éléments de rapport publiés directement vers des bibliothèques de documents SharePoint, la fonctionnalité de niveau de site **Synchronisation de fichiers de serveur de rapports** est très utile. La fonctionnalité de synchronisation de fichiers synchronise le catalogue du serveur de rapports avec les éléments des bibliothèques de documents à des intervalles plus fréquents. Pour plus d'informations, consultez [Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).  
  
##  <a name="bkmk_verify_installation"></a> Vérifier l'installation  
 Les mesures et procédures suggérées suivantes permettent de vérifier le déploiement de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.  
  
-   Consultez la section SharePoint dans la rubrique de contrôle [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).  
  
-   Dans une bibliothèque de documents SharePoint, créez un rapport de base [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui ne contient qu'une seule zone de texte, un titre par exemple. Le rapport ne contient aucune source de données ni aucun dataset. Le but est de vérifier que vous pouvez ouvrir le Générateur de rapports, créer un rapport de base et afficher un aperçu du rapport.  
  
     Enregistrez le rapport dans la bibliothèque de documents, puis exécutez le rapport depuis la bibliothèque. Pour plus d’informations sur la création de rapports avec le Générateur de rapports, consultez [Démarrer le Générateur de rapports](https://technet.microsoft.com/library/ms159221.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Applets de commande PowerShell pour le mode SharePoint de Reporting Services](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 feuille de route de @no__t 0Content : Installer et configurer SharePoint Server et SQL Server BI @ no__t-0 @ no__t-1  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Services Reporting Services SharePoint et applications de service](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
  
  
