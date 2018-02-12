---
title: Installer Machine Learning serveur autonome ou R Server autonome | Documents Microsoft
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 275bda79d9c8cb74d871a4d13612847dc58592e8
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone"></a>Installer Machine Learning Server (autonome) ou R Server (autonome)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le programme d’installation de SQL Server inclut la possibilité d’installer un serveur qui s’exécute en dehors de SQL Server d’apprentissage. Cette option peut être utile si vous avez besoin développer des solutions d’apprentissage machine de hautes performances qui peuvent utiliser les contextes de calcul à distance, ou qui peuvent être déployées sur plusieurs plateformes, notamment :
  
  + Une instance de SQL Server 2016 ou 2017 de serveur SQL où l’apprentissage automatique est activé
  + Une instance de serveur de R ou Machine Learning dans un cluster Hadoop ou Spark
  + R Server ou serveur d’apprentissage Machine dans Linux

Cet article décrit comment utiliser le programme d’installation de SQL Server pour installer la version autonome de Machine Learning Server ou Microsoft R Server. Si vous disposez d’une édition entreprise ou la Software Assurance, installez le serveur d’apprentissage autonome est gratuit.

+ [Installer R Server](#bkmk_installRServer) -utilise le programme d’installation de SQL Server 2016
+ [Installer le serveur de Machine Learning](#bkmk_installMLServer) -utilise le programme d’installation de SQL Server 2017
+ [Mise à niveau une instance existante de Microsoft R Server](#bkmk_upgrade)
+ [M’aider à déterminer les éléments à installer](#bkmk_tips)

##  <a name="bkmk_installMLServer"></a>Installer Server (autonome) d’apprentissage

Cette fonctionnalité requiert une licence d’entreprise ou l’équivalent pour **SQL Server 2017**.

Si vous avez installé une version antérieure de Microsoft R Server, nous vous recommandons de désinstaller tout d’abord.

Si l’ordinateur n’a pas accès à Internet, vous devez télécharger les programmes d’installation du composant à l’avance. Pour plus d’informations, consultez [l’installation des composants d’apprentissage machine sans accès à internet](./installing-ml-components-without-internet-access.md).

1. Exécutez le programme d’installation de SQL Server 2017.

2. Cliquez sur le **Installation** et sélectionnez **installation de la nouvelle Machine Learning Server (autonome)**.
    
     ![Installer Machine Learning serveur autonome](media/2017setup-installation-page-mlsvr.png "démarrer l’installation de la Machine Learning serveur autonome")

3. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence de SQL Server et sélectionnez une nouvelle installation.

4. Sur le **sélection des fonctionnalités** page, ce qui suit options doivent être déjà sélectionnées :

    - Microsoft Machine Learning Server (autonome)

    - R et Python est sélectionnées par défaut. Vous pouvez désélectionner les deux langages, mais nous vous recommandons d’installer au moins une des langues prises en charge.

     ![Installer Machine Learning serveur autonome](media/2017setup-features-page-mlsvr-rpy.png "démarrer l’installation de la Machine Learning serveur autonome")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si l’ordinateur est déjà Machine Learning Services est installé pour l’analytique des bases de données dans SQL Server. Cette opération crée les bibliothèques en double.
    > 
    > En outre, tandis que les scripts R ou Python en cours d’exécution dans SQL Server sont gérés par SQL Server, par conséquent, comme n’étant ne pas en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, serveur autonome machine learning n’a aucuns contraintes et peut interférer avec d’autres opérations de base de données . Enfin, l’accès à distance via une session RDP, qui est souvent utilisé pour une Opérationnalisation rapides, est généralement bloqué par les administrateurs de base de données.
    > 
    > Pour ces raisons, nous déconseillons généralement que vous installez Machine Learning Server (autonome) sur un ordinateur distinct à partir de la Machine Learning Services SQL Server.

5.  Accepter les termes du contrat de licence pour télécharger et installer les composants d’apprentissage automatique. Si vous installez les deux langages, un contrat de licence distinct est requis pour Microsoft R et pour Python.
    
     ![Contrat de licence de Python](media/2017setup-python-license.png "contrat de licence de Python")
    
    Installation de ces composants et les composants requis que peuvent nécessiter, peut prendre un certain temps. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**.

6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

Pour plus d’informations sur l’installation automatisée ou hors connexion, consultez [installer Microsoft R Server à partir de la ligne de commande](../../advanced-analytics/r/install-microsoft-r-server-from-the-command-line.md).

##  <a name="bkmk_installRServer"></a> Installer Microsoft R Server (autonome)

Cette fonctionnalité requiert une licence d’entreprise ou l’équivalent pour **SQL Server 2016**.

Si vous avez installé une version précédente de l’outils de Revolution Analytique ou les packages, vous devez tout d’abord les désinstaller. Consultez [la mise à niveau à partir d’une version antérieure de Microsoft R Server](#bkmk_Uninstall).

1. Exécutez le programme d’installation de SQL Server 2016. Nous vous recommandons d’installer Service Pack 1 ou version ultérieure.

2. Sur le **Installation** , cliquez sur **installation nouvelle R Server (autonome)**.
    
     ![Démarrer le programme d’installation de R Server autonome](media/2016-setup-installation-rsvr.png "démarrer le programme d’installation de R serveur autonome")
    
3.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
    **R Server (autonome)**  
    
    ![Fonctionnalité des sélections pour la version autonome du serveur R](media/2016setup-rserver-features.png "les sélections pour la version autonome du serveur R de fonctionnalités")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si vous exécutez le programme d’installation sur un ordinateur où R Services a déjà été installé pour l’analytique des bases de données dans SQL Server. Cette opération crée les bibliothèques en double.
    > 
    > Tandis que les scripts R en cours d’exécution dans SQL Server sont gérés par SQL Server, par conséquent, comme n’étant ne pas en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, le serveur R autonome n’a aucuns contraintes et peut interférer avec d’autres opérations de base de données.
    > 
    > En règle générale, nous recommandons que vous installez Machine Learning Server (autonome) sur un ordinateur distinct à partir de la Machine Learning Services SQL Server.

4.  Acceptez les termes du contrat de licence pour télécharger et installer Microsoft R Open. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**.
    
    Installation de ces composants et les composants requis que peuvent nécessiter, peut prendre un certain temps.
    
5.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

## <a name="bkmk_upgrade"></a>Mise à niveau une instance existante de R Server

Si vous avez installé une version antérieure de Microsoft R Server (autonome), vous pouvez mettre à niveau l’instance pour utiliser les dernières versions des composants R. La mise à niveau modifie également la stratégie de prise en charge pour utiliser la stratégie du cycle de vie de la logiciels modernes prennent en charge. Cela permet à l’instance mise à jour plus fréquemment, sur une autre planification de mises à jour de SQL Server.

1. Téléchargez le programme d’installation distinct basé sur Windows à partir des emplacements répertoriés ici : 

    + [Installer le serveur d’apprentissage pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [Installer R Server 9.1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

2. Exécutez le programme d’installation et suivez les instructions. Dans la page où vous sélectionnez les composants à installer, sélectionnez chaque instance de serveur R que vous souhaitez mettre à niveau.

## <a name ="bkmk_tips"></a>Suivi et des conseils pour l’installation

Cette section fournit des informations supplémentaires concernant le programme d’installation.

### <a name="which-version-should-i-install"></a>Quelle version dois-je installer ?

+ **Microsoft R Server** proposé pour la première fois dans le cadre de SQL Server 2016 et prend en charge le langage R. La dernière version de Microsoft R Server a été 9.0.1.

+ **Microsoft Machine Learning Server** est la dernière version, ce qui a été publiée avec SQL Server 2017 et propose de nombreuses mises à jour, y compris la prise en charge pour Python. À jour cumulative 1 pour SQL Server 2017 a été libérée, ce qui inclut la version 9.2.1.24 du serveur de Machine Learning. Nous vous recommandons de cette mise à jour si vous souhaitez que les API de Python plus récente.

+ **La mise à niveau en place**: le programme d’installation requiert une licence de SQL Server et les mises à niveau sont généralement alignées avec la cadence de publication SQL Server. Vous avez ainsi assuré que vos outils de développement sont en phase avec la version s’exécutant dans le contexte de calcul de SQL Server. Toutefois, vous pouvez utiliser le programme d’installation distinct basé sur Windows pour obtenir des mises à jour plus fréquentes, sous la stratégie de prise en charge du cycle de vie logiciel moderne. Vous pouvez également utiliser ce programme d’installation pour mettre à niveau une instance de SQL Server 2016 ou SQL Server 2017.

### <a name="default-installation-folders"></a>Dossiers d’installation par défaut

Lorsque vous installez R Server ou un serveur d’apprentissage Machine à l’aide du programme d’installation de SQL Server, les bibliothèques R sont installés dans un dossier associé à la version de SQL Server que vous avez utilisé pour le programme d’installation. Dans ce dossier, vous y trouverez également des exemples de données, la documentation pour les packages de base R et documentation des outils de R et de runtime.

Toutefois, si vous installez à l’aide du programme d’installation Windows distinct, ou si vous mettez à niveau à l’aide du programme d’installation Windows distinct, les bibliothèques R sont installés dans un dossier différent.

Pour référence, si vous avez installé une instance de SQL Server avec R Services (de-de base de données) ou Machine Learning (de-de base de données), et cette instance est sur le même ordinateur, les bibliothèques R et les outils sont installés par défaut dans un dossier différent.

Le tableau suivant répertorie les chemins d’accès pour chaque installation.

|Version| Méthode d’installation | Dossier par défaut|
|----|----|----|
|R Server (autonome) |Assistant Installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (autonome) |Le programme d’installation de Windows autonome|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (autonome) |  Assistant Installation de SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (autonome) |  Le programme d’installation de Windows autonome |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (dans la base de données) |Assistant Installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (en base de données) |Assistant Installation de SQL Server 2017|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`ou`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

### <a name="development-tools"></a>Outils de développement

Un développement IDE n’est pas installé dans le cadre du programme d’installation. Des outils supplémentaires ne sont pas requis, comme tous les outils standards sont inclus qui serait fournie avec une distribution de R ou Python.

Nous vous recommandons d’essayer la nouvelle version de [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]. Visual Studio prend en charge à la fois R et Python, ainsi que les outils de développement de base de données, la connectivité avec SQL Server et des Outils BI. Toutefois, vous pouvez utiliser n’importe quel environnement de développement par défaut, y compris RStudio.

## <a name="troubleshooting"></a>Dépannage

Cette section répertorie certains problèmes courants qui peuvent survenir lors de l’installation du serveur d’apprentissage Machine ou R.

### <a name="incompatible-version-of-r-client-and-r-server"></a>Version incompatible de R Client et de R Server

Si vous installez Microsoft R Client et l’utiliser pour exécuter R dans un contexte de calcul de SQL Server à distance, vous pouvez obtenir ce type d’erreur :

*Version9.0.0 du client de Microsoft R sont en cours d’exécution sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 Microsoft R Server. Téléchargez et installez une version compatible.*

Dans SQL Server 2016, il était nécessaire que la version de R en cours d’exécution dans SQL Server R Services être exactement le même que les bibliothèques dans le Client Microsoft R. Cette exigence a été supprimée dans les versions ultérieures. Toutefois, nous vous recommandons de vous toujours obtenez les dernières versions des composants d’apprentissage et d’installer tous les service packs. 

Si vous avez une version antérieure de Microsoft R Server et que vous avez besoin assurer la compatibilité avec le Client Microsoft R 9.0.0, installer les mises à jour qui sont décrites dans cette [article du support technique](https://support.microsoft.com/kb/3210262).

### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Installation de Microsoft R Server sur une instance de SQL Server installée sur Windows Core

Dans la version RTM de SQL Server 2016, il a été un problème connu lors de l’ajout de Microsoft R Server pour une instance sur l’édition de Windows Server Core. Ce problème a été résolu.

Si vous rencontrez ce problème, vous pouvez appliquer le correctif décrit dans [KB3164398](https://support.microsoft.com/kb/3164398) pour ajouter la fonctionnalité de R à l’instance existante sur Windows Server Core.   Pour plus d’informations, consultez [Impossible d’installation Microsoft R Server (autonome) sur un système d’exploitation Windows Server Core](https://support.microsoft.com/kb/3168691).

###  <a name="bkmk_Uninstall"></a>La mise à niveau à partir d’une version antérieure de Microsoft R Server

Si vous avez installé une version préliminaire de Microsoft R Server, commencez par la désinstaller avant de pouvoir mettre à niveau vers une version plus récente.

**Pour installer R Server (autonome)**

1.  Dans le **Panneau de configuration**, cliquez sur **Ajout/Suppression de programmes**, et sélectionnez `Microsoft SQL Server 2016 <version number>`.

2.  Dans la boîte de dialogue proposant les options **Ajouter**, **Réparer**ou **Supprimer** les composants, sélectionnez **Supprimer**.
  
3.  Sur la page **Sélectionner les fonctionnalités** sous **Composants partagés**, sélectionnez **R Server (autonome)**. Cliquez sur **Suivant**, puis sur **Terminer** pour désinstaller les composants sélectionnés uniquement.

### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L’installation échoue avec l’erreur : « Seul un produit Revolution Enterprise peut être installé à la fois. »

Vous pouvez rencontrer cette erreur si votre installation de produits Revolution Analytics est ancienne ou si vous disposez d’une version préliminaire de SQL Server R Services. Vous devez désinstaller toute version précédente avant de pouvoir installer une version plus récente de Microsoft R Server. L’installation côte à côte avec d’autres versions des outils Revolution Enterprise n’est pas prise en charge.

Cependant, les installations côte à côte sont prises en charge quand R Server (autonome) est utilisé avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] ou SQL Server 2016.

### <a name="unable-to-uninstall-older-components"></a>Impossible de désinstaller les composants plus anciens

Si vous rencontrez des problèmes de suppression d’une version antérieure, vous devrez peut-être modifier le Registre pour supprimer les clés associées.

> [!IMPORTANT]
> Ce problème s’applique uniquement si vous avez installé une version préliminaire de Microsoft R Server ou une version CTP de SQL Server 2016 R Services.
  
1. Ouvrez le Registre Windows et recherchez cette clé : `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.
2. Supprimez toutes les entrées suivantes, le cas échéant, et si la clé contient uniquement la valeur `sEstimatedSize2`:
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (pour 8.0.2)
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (pour 8.0.1)
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (pour 8.0.0)
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (pour 7.5.0)
  
## <a name="see-also"></a>Voir aussi

[Machine Learning Server (Autonome)](../../advanced-analytics/r/r-server-standalone.md)
