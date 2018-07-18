---
title: Installer SQL Server 2016 R Server (autonome) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e5457698120536247ad1823b842bb1b8e52b484d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979281"
---
# <a name="install-sql-server-2016-r-server-standalone"></a>Installer SQL Server 2016 R Server (autonome)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment utiliser le programme d’installation de SQL Server 2016 à installer la version autonome de **SQL Server 2016 R Server**.

## <a name="bkmk_prereqs"> </a> Liste de vérification de préinstallation

SQL Server 2016 est nécessaire. Si vous avez SQL Server 2017, vous devez installer [SQL Server 2017 Machine Learning Server (autonome)](sql-machine-learning-standalone-windows-install.md) à la place.

Si vous avez installé n’importe quelle version précédente des outils de Revolution Analytique ou packages, vous devez tout d’abord les désinstaller. 

## <a name="get-the-installation-media"></a>Obtenir le média d’installation

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Installer le correctif obligatoire 

Microsoft a identifié un problème avec la version spécifique des fichiers binaires Microsoft VC++ 2013 Runtime qui sont installés en tant que composants requis par SQL Server. Si cette mise à jour des fichiers binaires du runtime VC n’est pas installée, SQL Server risque de rencontrer des problèmes de stabilité dans certains scénarios. Avant d’installer SQL Server, suivez les instructions données dans [Notes de publication de SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) pour voir si votre ordinateur nécessite un correctif pour les fichiers binaires du runtime VC.  

## <a name="run-setup"></a>Exécutez le programme d’installation

Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.

1. Démarrer l’Assistant Installation de SQL Server 2016. Nous vous recommandons d’installer Service Pack 1 ou version ultérieure.

2. Sur le **Installation** , cliquez sur **installation nouvelle R Server (autonome)**.
    
     ![Démarrer le programme d’installation de R Server (autonome)](media/2016-setup-installation-rsvr.png "démarrer le programme d’installation de R Server (autonome)")
    
3.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
    **R Server (autonome)**  
    
    ![Sélections pour R Server (autonome) de fonctionnalités](media/2016setup-rserver-features.png "fonctionnalité sélections pour R Server (autonome)")
    
    Toutes les autres options peuvent être ignorées. 
    
    > [!NOTE]
    > Évitez d’installer le **fonctionnalités partagées** si vous exécutez le programme d’installation sur un ordinateur où R Services a déjà été installé pour l’analytique en base de données de SQL Server. Cela crée des bibliothèques en double.
    > 
    > Tandis que les scripts R en cours d’exécution dans SQL Server sont gérés par SQL Server pour autant en conflit avec la mémoire utilisée par d’autres services de moteur de base de données, R Server autonome ne comporte aucune contrainte de ce type et peut interférer avec d’autres opérations de base de données.
    > 
    > Nous recommandons généralement que vous installez R Server (autonome) sur un ordinateur distinct à partir de SQL Server R Services (en base de données).

4.  Acceptez les termes du contrat de licence pour télécharger et installer Microsoft R Open. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**.
    
    Installation de ces composants et les composants requis que peuvent nécessiter, peut prendre un certain temps.
    
5.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.

## <a name="default-installation-folders"></a>Dossiers d’installation par défaut

Lorsque vous installez R Server à l’aide du programme d’installation de SQL Server, les bibliothèques R sont installés dans un dossier associé à la version de SQL Server que vous avez utilisé pour le programme d’installation. Dans ce dossier, vous trouverez également exemples de données, la documentation pour les packages de base R et documentation des outils de R et de l’exécution.

Toutefois, si vous avez installé Microsoft R Server à l’aide du programme d’installation Windows (pas d’installation de SQL) distinct, ou si vous mettez à niveau à l’aide du programme d’installation Windows distinct, les bibliothèques R sont installés dans un dossier différent.

Bien que nous vous déconseillons, si vous avez également installé une instance de SQL Server avec R Services (en base de données) sur le même ordinateur, une deuxième copie de bibliothèques et outils R sont installés dans un dossier différent.

Le tableau suivant répertorie les chemins d’accès pour chaque installation.

|Version| Méthode d’installation | Dossier par défaut|
|----|----|----|
|R Server (autonome) |Assistant d’installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (autonome) |Le programme d’installation de Windows autonome|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (autonome) |  Assistant d’installation de SQL Server 2017, avec l’option de langage R |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (autonome) |  Assistant d’installation de SQL Server 2017, avec l’option de langage Python |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning Server (autonome) |  Le programme d’installation de Windows autonome |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (dans la base de données) |Assistant d’installation de SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (en base de données) |Assistant d’installation de SQL Server 2017, avec l’option de langage R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning Services (en base de données) |Assistant d’installation de SQL Server 2017, avec l’option de langage Python| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>Outils de développement

Un IDE de développement n’est pas installé dans le cadre du programme d’installation. Outils supplémentaires ne sont pas nécessaires, comme tous les outils standard sont inclus qui serait fournie avec une distribution de R ou Python.

Nous vous recommandons d’essayer la nouvelle version de [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] ou [Python pour Visual Studio](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio prend en charge à la fois R et Python, mais aussi les outils de développement de base de données, la connectivité avec SQL Server et les outils décisionnels. Toutefois, vous pouvez utiliser n’importe quel environnement de développement préféré, notamment RStudio.
  
## <a name="get-help"></a>Obtenir de l’aide

Besoin d’aide avec l’installation ou mise à niveau ? Pour obtenir des réponses aux questions courantes et les problèmes connus, consultez l’article suivant :

* [Mise à niveau et installation FAQ - Services Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Pour vérifier l’état d’installation de l’instance et résoudre les problèmes courants, essayez ces rapports personnalisés.

* [Rapports personnalisés pour SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Étapes suivantes

Aux développeurs R peuvent démarrer avec des exemples simples et apprendre les bases du fonctionne de R avec SQL Server. Pour votre prochaine étape, consultez les liens suivants :

+ [Didacticiel : Exécuter R dans T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).
+ [Didacticiel : De base de données analytique pour les développeurs R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Pour afficher des exemples d’apprentissage qui sont basées sur des scénarios réels, consultez [d’apprentissage didacticiels](../tutorials/machine-learning-services-tutorials.md).

