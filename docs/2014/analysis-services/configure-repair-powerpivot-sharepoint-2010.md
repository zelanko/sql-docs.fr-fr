---
title: Configurer ou réparer PowerPivot pour SharePoint 2010 (outil de Configuration PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d61f49c5-efaa-4455-98f2-8c293fa50046
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 350aadcdd44dcc4424b94792286a7421e2613b2e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66087384"
---
# <a name="configure-or-repair-powerpivot-for-sharepoint-2010-powerpivot-configuration-tool"></a>Configurer ou réparer PowerPivot pour SharePoint 2010 (outil de configuration de PowerPivot)
  Utilisez l'Outil de configuration de PowerPivot pour configurer ou réparer une installation de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] PowerPivot pour SharePoint 2010. L'outil de configuration commence par analyser le système, puis retourne une liste d'actions nécessaires pour achever ou réparer votre installation. L'Assistant Installation de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] installe l'outil de configuration de PowerPivot pour SharePoint 2010 et un outil de configuration de PowerPivot pour SharePoint 2013. Cette rubrique décrit l'outil de configuration de PowerPivot pour SharePoint 2010. Pour plus d’informations sur SharePoint 2010, consultez [configurer ou réparer PowerPivot pour SharePoint 2013 &#40;outil de Configuration PowerPivot&#41;](power-pivot-sharepoint/configure-or-repair-power-pivot-for-sharepoint-2013.md).  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
 
  
##  <a name="bkmk_before"></a> Avant de commencer  
 L'outil de configuration PowerPivot pour SharePoint 2010 recherche les fichiers programme, les paramètres du Registre et les ports disponibles. Pour optimiser l'utilisation de ces outils, vérifiez les points suivants.  
  
-   Exigences générales pour exécuter l'outil de configuration [PowerPivot Configuration Tools](power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
-   PowerPivot pour SharePoint 2010 requiert que les applications Web soient configurées pour l'authentification en mode classique. Si l'outil de configuration de PowerPivot pour SharePoint 2010 crée l'application pour vous, celle-ci est configurée en mode classique.  
  
-   Le port 80 doit être disponible afin que l'une des tâches sélectionnées demande à l'outil de configuration de créer et configurer une application Web.  
  
##  <a name="bkmk_using"></a> À l’aide de l’outil de Configuration PowerPivot  
 La première page de l'outil fournit un résumé des valeurs d'entrée utilisées pour configurer la batterie de serveurs SharePoint. En plus des valeurs d'entrée fournies, des valeurs par défaut sont utilisées pour configurer le système. Des noms par défaut sont utilisés pour les applications de service, les bases de données d'application de service et les propriétés d'application de service.  
  
> [!TIP]  
>  Si l'outil de configuration PowerPivot analyse l'ordinateur et retourne une liste de tâches vide dans le volet gauche, aucune configuration de fonctionnalités ou de paramètres n'est requise. Pour modifier la configuration de SharePoint ou PowerPivot, utilisez Windows PowerShell ou les pages d'administration dans l'Administration centrale de SharePoint. Pour plus d’informations, consultez [d’Administration de serveur PowerPivot et de Configuration dans l’Administration centrale](power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
 Les valeurs des comptes de service sont utilisées pour plusieurs services. Par exemple, l'outil de configuration PowerPivot utilise le compte par défaut sur la première page pour configurer toutes les identités du pool d'applications. Vous pouvez modifier ces comptes ultérieurement en modifiant les propriétés d'application de service dans l'Administration centrale.  
  
-   L'exception à cette règle dans l'outil de configuration de PowerPivot pour SharePoint 2010 est le compte de service Analysis Services. Ce compte est spécifié pendant l’installation, et que vous tapez un mot de passe pour ce compte dans le **inscrire SQL Server Analysis Services (PowerPivot sur le serveur Local)** action. La page de résumé n'incluant pas de champ pour ce mot de passe, veillez à le saisir sur la page de cette action.  
  
 L'outil fournit une interface avec onglets qui comporte les entrées de paramètre, le script Windows PowerShell et les messages d'état.  
  
 L'outil de configuration PowerPivot utilise Windows PowerShell pour configurer le serveur. Vous pouvez cliquer sur le **Script** onglet pour consulter le script Windows PowerShell le.  
  
 ![Interface utilisateur de l’outil configuration](media/ssas-pctui.gif "interface utilisateur d’outil de Configuration")  
  
##  <a name="bkmk_steps"></a> Étapes de configuration  
 Le lien vers l'outil de configuration est visible uniquement lorsque PowerPivot pour SharePoint 2010 est installé sur le serveur local.  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, cliquez sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Outil de configuration PowerPivot**.  
  
2.  Cliquez sur **Configurer ou réparer PowerPivot pour SharePoint**.  
  
3.  Affichez la fenêtre en plein écran. Vous devez voir une barre d'icônes en bas de la fenêtre qui comprend les commandes **Valider**, **Exécuter**et **Quitter** .  
  
4.  **Compte par défaut :** Sous l’onglet Paramètres, tapez un compte d’utilisateur de domaine pour le **nom d’utilisateur de compte par défaut**. Ce compte est utilisé pour configurer des services essentiels, notamment le pool d'applications de service PowerPivot. Ne spécifiez pas un compte intégré tel que Service réseau ou Système local. L'outil bloque les configurations qui spécifient des comptes intégrés.  
  
     **Phrase secrète :** entrez une phrase secrète. Pour une nouvelle batterie de serveurs SharePoint, la phrase secrète est utilisée chaque fois que vous ajoutez un serveur ou une application à la batterie de serveurs SharePoint. Si la batterie existe déjà, entrez la phrase secrète qui vous permet d'ajouter une application de serveur à la batterie.  
  
5.  **Port :** Si vous le souhaitez, tapez un numéro de port pour se connecter à l’application web Administration centrale ou utilisez le nombre généré de manière aléatoire fourni. L'outil de configuration vérifie que le nombre est disponible avant de le proposer comme option.  
  
6.  Cliquez sur **inscrire SQL Server Analysis Services (PowerPivot) sur le serveur Local**.  
  
     Entrez le mot de passe du compte de service Analysis Services.  
  
7.  Éventuellement, examinez les valeurs d'entrée restantes utilisées pour effectuer chaque action. Pour plus d'informations sur chacune d'elles, consultez [Valeurs d'entrée utilisées pour configurer le serveur](#bkmk_input) dans cette rubrique.  
  
8.  Éventuellement, supprimez toutes les actions que vous ne souhaitez pas traiter. Par exemple, si vous souhaitez configurer le service Banque d'informations sécurisé ultérieurement, cliquez sur **Configurer le service Banque d'informations sécurisé**, puis désactivez la case à cocher **Inclure cette action dans la liste des tâches**.  
  
9. Cliquez sur **Valider** pour vérifier que l'outil dispose d'informations suffisantes pour traiter les actions de la liste.  
  
    > [!NOTE]  
    >  Si vous obtenez une erreur de configuration de la batterie de serveurs, cela peut être dû au fait que SharePoint 2010 Server SP1 n'est pas installé.  
  
10. Cliquez sur **Exécuter** pour traiter toutes les actions de la liste des tâches. Le bouton **Exécuter** est activé après avoir validé les actions. Si **Exécuter** n'est pas activé, commencez par cliquer sur **Valider** .  
  
11. [Verify a PowerPivot for SharePoint Installation](instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md).  
  
##  <a name="bkmk_input"></a> Valeurs d'entrée utilisées pour configurer le serveur  
 L'outil de configuration de PowerPivot utilise une combinaison de valeurs d'entrée que vous tapez et de valeurs par défaut qu'il détecte ou utilise automatiquement.  
  
 La liste des actions répertoriées dans l'outil de configuration dépend de la configuration actuelle des batteries de serveurs SharePoint. Par exemple, si la batterie de serveurs SharePoint est déjà configurée, aucune action n'est répertoriée dans l'outil. Vous pouvez exécuter l'outil à tout moment pour configurer, réparer, ou détecter des erreurs de configuration. Si des services requis, tels qu'Excel Services ou le service Banque d'informations sécurisé, ne s'exécutent pas dans la batterie, l'outil détecte les services manquants et fournit des options permettant de les activer. Si aucune action n'est requise, la liste des tâches est vide.  
  
 Le tableau suivant décrit les valeurs utilisées pour configurer le serveur.  
  
|Radiomessagerie|Valeur d'entrée|`Source`|Description|  
|----------|-----------------|------------|-----------------|  
|**Configurer ou réparer PowerPivot pour SharePoint**|Compte par défaut|Utilisateur actuel|Le compte par défaut est un compte d'utilisateur de domaine Windows utilisé pour configurer des services partagés dans la batterie. Il est utilisé pour configurer l'application de service PowerPivot, le service Banque d'informations sécurisé, Excel Services, l'identité du pool d'applications Web, l'administrateur de collection de sites, et le compte d'actualisation sans assistance des données PowerPivot.<br /><br /> Par défaut, l'outil utilise le compte de domaine de l'utilisateur actuel. À moins de configurer un serveur à des fins d'évaluation, vous devez le remplacer par un autre compte d'utilisateur de domaine.<br /><br /> Vous pouvez aussi modifier les identités de service ultérieurement, à l'aide de l'Administration centrale.<br /><br /> Éventuellement, dans l'outil de configuration de PowerPivot, vous pouvez spécifier des comptes dédiés pour ce qui suit :<br /><br /> Application Web, à l'aide de la page **Créer une application Web par défaut** (en supposant que l'outil crée une application Web pour la batterie).<br /><br /> Compte d’actualisation des données sans assistance, à l’aide de PowerPivot le **créer un compte sans assistance pour l’actualisation des données** page dans cet outil.|  
||Serveur de base de données|Instance nommée PowerPivot locale, si disponible|Si une instance du moteur de base de données est installée en tant qu'instance nommée PowerPivot, l'outil renseignera le champ du serveur de base de données avec cette instance. Si vous n'avez pas installé le moteur de base de données, ce champ est vide. Vous devez fournir une instance. Il peut s'agir de n'importe quelle version ou édition de SQL Server prise en charge pour les batteries de serveurs SharePoint.|  
||Phrase secrète|Entrée utilisateur|Si vous créez une nouvelle batterie, la phrase secrète que vous entrez sera la phrase secrète pour la batterie. Si vous ajoutez PowerPivot pour SharePoint à une batterie de serveurs existante, vous devez fournir la phrase secrète qui a été définie pour la batterie lors de sa création.|  
||Port de l'Administration centrale de SharePoint|Par défaut, si nécessaire|Si la batterie de serveurs n'est pas configurée, l'outil fournit des options pour la création de la batterie de serveurs, notamment pour la création d'un point de terminaison HTTP dans l'Administration centrale. Il choisit par défaut un numéro de port généré de manière aléatoire qui n'est pas encore utilisé.|  
|**Configurer une nouvelle batterie de serveurs**|Serveur de base de données<br /><br /> Compte de batterie de serveurs<br /><br /> Phrase secrète<br /><br /> Port de l'Administration centrale de SharePoint|Par défaut, si nécessaire|Valeur par défaut de paramètres que vous avez entrés dans dans la page principale.|  
|**Configurer l’Instance de Service Local**|Mot de passe du compte de service Analysis Services|Entrée utilisateur|Vous devez taper le mot de passe du compte de service Analysis Services dans le **inscrire SQL Server Analysis Services (PowerPivot) sur le serveur Local** page.<br /><br /> Le compte de service a été spécifié pendant l'installation. Vous devez maintenant taper le mot de passe comme entrée pour inscrire l'instance de service local avec SharePoint.|  
|**Créer l’Application de Service PowerPivot**|Nom de l'application de service PowerPivot|Par défaut|Le nom par défaut est celui de l'application de service PowerPivot par défaut. Vous pouvez le remplacer par une valeur différente dans l'outil.|  
||Serveur de base de données d'application de service PowerPivot|Par défaut|Serveur de base de données qui héberge la base de données d'application de service PowerPivot. Le nom par défaut du serveur est le même que celui du serveur de base de données utilisé pour la batterie. Vous pouvez le remplacer par une valeur différente dans l'outil.|  
||Nom de la base de données d'application de service PowerPivot|Par défaut|Le nom de la base de données par défaut est basé sur le nom de l'application de service, suivi d'un GUID pour garantir un nom unique. Vous pouvez le remplacer par une valeur différente dans l'outil.|  
||Mettre les classeurs à niveau pour activer l'actualisation des données|Entrée utilisateur|L'actualisation des données échoue et n'est pas prise en charge pour les classeurs SQL Server 2008 R2 PowerPivot. L’option **mettre les classeurs pour activer les données actualisation** met à niveau les classeurs vers la version de SQL Server 2012 PowerPivot.|  
|**Créer une application Web par défaut**|Nom de l'application Web|Par défaut, si nécessaire|S'il n'existe aucune application Web, l'outil en crée une. L’application web est configurée pour l’authentification en mode classique et écouter sur **le port 80**. La taille maximale de téléchargement de fichier a la valeur 2047 Mo, qui est la valeur maximale autorisée par SharePoint. La taille maximale de téléchargement de fichiers est adaptée aux fichiers PowerPivot volumineux.|  
||URL|Par défaut, si nécessaire|L'outil crée une URL basée sur le nom du serveur, en respectant les mêmes conventions d'affectation de noms de fichier que SharePoint.|  
||Pool d'applications Web|Par défaut, si nécessaire|L'outil crée un pool d'applications par défaut dans IIS.|  
||Compte et mot de passe du pool d'applications Web|Par défaut, si nécessaire|Le compte du pool d'applications est basé sur le compte par défaut, mais vous pouvez le remplacer dans l'outil.|  
||Serveur de la base de données d'application Web|Par défaut, si nécessaire|L'instance de base de données par défaut est pré-sélectionnée pour stocker la base de données d'application, mais vous pouvez spécifier une autre instance de SQL Server dans l'outil.|  
||Nom de la base de données d'application Web|Par défaut, si nécessaire|Le nom de la base de données est basé sur les conventions d'affectation de noms de fichier de SharePoint, mais vous pouvez choisir un autre nom.|  
|**Déployer une solution d'application Web**|URL|Par défaut, si nécessaire|L'URL par défaut provient de l'application Web par défaut.|  
||Taille maximale de fichier (en Mo)|Par défaut, si nécessaire|Le paramètre par défaut est 2047. Les bibliothèques de documents SharePoint sont également limitées en taille et le paramètre PowerPivot ne doit pas dépasser le paramètre de la bibliothèque de documents. Pour plus d’informations, consultez [configurer une taille de téléchargement de fichier maximale &#40;PowerPivot pour SharePoint&#41;](power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).|  
|**Créer une collection de sites**|Administrateur de site|Par défaut, si nécessaire|L'outil utilise le compte par défaut. Vous pouvez le remplacer dans la page **Créer une collection de sites** .|  
||Adresse de messagerie du contact|Par défaut, si nécessaire|Si Microsoft Outlook est configuré sur le serveur, l'outil utilisera l'adresse de messagerie de l'utilisateur actuel. Sinon, une valeur d'espace réservé est utilisée.|  
||URL du site|Par défaut, si nécessaire|L'outil crée l'URL de site, en respectant les mêmes conventions d'affectation de noms d'URL que SharePoint.|  
||Titre du site|Par défaut, si nécessaire|L'outil ajoute **Site PowerPivot** comme titre par défaut.|  
|**Activer une fonctionnalité PowerPivot dans une Collection de sites**|URL du site||URL de la collection de sites pour laquelle vous activez les fonctionnalités PowerPivot.|  
||Activer la fonctionnalité Premium pour ce site||Activer la fonctionnalité de site SharePoint « PremiumSite ».|  
|**Créer une application du service Banque d'informations sécurisé**|Nom d'application de service||Tapez le nom de l'application du Service Banque d'informations sécurisé.|  
||Serveur de base de données||Tapez le nom du serveur de base de données à utiliser pour l'application du Service Banque d'informations sécurisé.|  
|**Créer un proxy d'application du service Banque d'informations sécurisé**|Nom d'application de service||Tapez le nom de l'application du Service Banque d'informations sécurisé.|  
||Proxy d'application de service||Tapez le nom du proxy du Service Banque d'informations sécurisé.  Le nom apparaît dans le groupe de connexions par défaut qui associe les applications aux applications Web de contenu SharePoint.|  
|**Mettre à jour la clé principale du service Banque d'informations sécurisé**|Proxy d'application de service||Entrer le nom du proxy du Service Banque d'informations sécurisé|  
||Phrase secrète||La clé principale est utilisée pour le chiffrement des données. Par défaut, la phrase secrète utilisée pour générer cette clé est la même que celle utilisée pour configurer de nouveaux serveurs dans la batterie de serveurs. Vous pouvez remplacer la phrase secrète par défaut par une phrase secrète unique.|  
|**Créer sans assistance un compte pour**|ID de l'application cible||L'ID d'application peut être du texte descriptif.|  
||Nom convivial pour l'application cible|||  
||Nom d'utilisateur et mot de passe du compte sans assistance||Tapez les informations d'identification d'un compte d'utilisateur Windows utilisé par l'application cible et pour exécuter l'actualisation des données sans assistance.|  
||URL du site||Tapez l'URL du site de la collection de sites associée à l'application cible. Pour associer d'autres collections de sites, utilisez l'Administration centrale de SharePoint.|  
|**Créer une application de service Excel Services**|Nom d'application de service||Entrez un nom pour l'application de service. Une base de données portant le même nom sera créé sur le serveur de base de données de la batterie de serveurs SharePoint.|  
|**Ajouter MSOLAP.5 en tant que fournisseur approuvé**|Nom d'application de service||Excel Services dans SharePoint 2010 utilise le fournisseur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] OLE DB pour la connexion aux données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cette étape ajoute le fournisseur OLE DB installé avec PowerPivot pour SharePoint en tant que fournisseur approuvé dans Excel Services.|  
||Nom du serveur PowerPivot|||  
|||||  
  
 Si l'outil de configuration PowerPivot crée la batterie, il crée les bases de données requises sur le serveur de base de données, en respectant les mêmes conventions d'affectation de noms de fichier que SharePoint. Vous ne pouvez pas modifier le nom de la base de données de la batterie de serveurs.  
  
 Si l'outil crée une collection de sites, il crée une base de données de contenu sur le serveur de base de données, en respectant les mêmes conventions d'affectation de noms de fichier que SharePoint. Vous ne pouvez pas modifier le nom de la base de données de contenu.  
  
##  <a name="bkmk_nextsteps"></a> Étapes suivantes  
 Une fois que vous avez terminé l'installation d'un serveur, vous devez effectuer plusieurs tâches de post-installation :  
  
-   Accordez les autorisations SharePoint aux individus et aux groupes. Cette tâche est nécessaire pour permettre l'accès aux sites et au contenu.  
  
-   Modifiez les identités du pool d'applications de service pour exécuter le programme sous un autre compte. La spécification d'identités différentes pour les services et les applications est une meilleure pratique SharePoint recommandée pour un déploiement sécurisé.  
  
-   Créez des sites de confiance supplémentaires dans Excel Services afin que vous puissiez varier au mieux les autorisations et les paramètres de configuration pour l'accès aux données PowerPivot.  
  
-   Installez ADO.NET Data Services 3.5 SP1 pour permettre l'exportation de flux de données à partir de listes SharePoint.  
  
-   Installez les fournisseurs de données les plus courants pour permettre l'actualisation des données côté serveur.  
  
-   Téléchargez l'outil de création PowerPivot vers votre station de travail pour créer un classeur PowerPivot puis le publier sur SharePoint. L'installation de l'outil et la publication d'un classeur PowerPivot complètent le cycle d'installation en vérifiant l'interopérabilité des composants serveur que vous venez d'installer.  
  
### <a name="grant-sharepoint-permissions-to-workbook-users"></a>Accorder des autorisations SharePoint aux utilisateurs des classeurs  
 Les utilisateurs ont besoin d'autorisations SharePoint pour pouvoir publier ou consulter des classeurs. Veillez à accorder **vue** autorisations aux utilisateurs qui ont besoin de consulter des classeurs publiés et **Contribute** autorisations aux utilisateurs qui publient ou gèrent des classeurs. Vous devez être administrateur de collection de sites pour pouvoir accorder des autorisations.  
  
1.  Dans le site, cliquez sur **Actions du Site**.  
  
2.  Cliquez sur **autorisations du Site**.  
  
3.  Créez autant de groupes que nécessaire si vous souhaitez configurer un ensemble d'utilisateurs ayant des autorisations de **Collaboration** et un groupe différent d'utilisateurs ayant uniquement des autorisations d' **Affichage** .  
  
4.  Entrez les comptes d'utilisateur ou de groupe de domaine Windows qui doivent appartenir aux groupes. Comme précédemment, n'utilisez pas d'adresses de messagerie ni de groupe de distribution si l'application est configurée pour une authentification classique.  
  
### <a name="install-adonet-data-services-35-sp1"></a>Installer ADO.NET Data Services 3.5 SP1  
 ADO.NET Data Services est requis pour une exportation de flux de données de listes SharePoint. SharePoint 2010 n'inclut pas ce composant dans le programme PrerequisiteInstaller requis pour SharePoint. Par conséquent, vous devez l'installer manuellement.  
  
1.  Accédez à la documentation relative à la configuration requise matérielle et logicielle pour SharePoint 2010, [déterminer la configuration matérielle et logicielle requise (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  Dans Installer les logiciels requis, recherchez le lien pour ADO.NET Data Services 3.5 correspondant au système d'exploitation que vous utilisez.  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
### <a name="install-data-providers-used-in-data-refresh-and-check-user-permissions"></a>Installer les fournisseurs de données utilisés dans l'actualisation des données et vérifier les autorisations utilisateur  
 L'actualisation des données côté serveur autorise des utilisateurs à ré-importer des données mises à jour en mode sans assistance. Pour que l'actualisation des données réussisse, le serveur doit avoir le même fournisseur de données que celui utilisé à l'origine pour importer les données. De plus, le compte d'utilisateur sous lequel l'actualisation des données s'exécute requiert souvent des autorisations de lecture sur les sources de données externes. Veillez à vérifier les configurations requises pour l'activation et la configuration de l'actualisation des données afin de garantir le résultat. Pour plus d’informations, consultez [d’actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).  
  
### <a name="change-application-pool-and-service-identities-in-sharepoint"></a>Modifier les identités de pool d'applications et de service dans SharePoint  
 L'outil de configuration PowerPivot comprend des fonctionnalités de batterie, des applications et des services à exécuter sous un compte unique. Cela simplifie l'installation, mais ne produit pas un déploiement conforme aux exigences de sécurité d'une batterie de serveurs SharePoint. Pour créer un déploiement plus fiable, modifiez les identités de pools d'applications et de services pour qu'ils s'exécutent sous des comptes différents, une fois l'installation terminée. Pour plus d’informations, consultez [configurer les comptes de Service PowerPivot](power-pivot-sharepoint/configure-power-pivot-service-accounts.md).  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Créer des sites de confiance supplémentaires dans Excel Services  
 Vous pouvez ajouter des sites de confiance dans Excel Services pour varier les autorisations et les paramètres de configuration sur les sites qui fournissent des classeurs Excel et des données PowerPivot. Pour plus d'informations, consultez [Créer un emplacement approuvé pour les sites PowerPivot dans l'Administration centrale](power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
### <a name="add-servers-or-applications"></a>Ajouter des serveurs ou des applications  
 Avec le temps, si vous déterminez que des capacités supplémentaires de stockage et de traitement des données sont nécessaires, ajoutez une deuxième instance de serveur PowerPivot pour SharePoint à la batterie de serveurs. Pour obtenir des instructions, consultez [liste de vérification de déploiement : Montée en puissance en ajoutant des serveurs PowerPivot à une batterie de serveurs SharePoint 2010](../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 ![Paramètres SharePoint](media/as-sharepoint2013-settings-gear.gif "paramètres SharePoint") [envoyer des commentaires et des informations via Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de Configuration de PowerPivot](power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
