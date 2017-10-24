---
title: "Créer un serveur R autonome | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4f39a03ecf7b74e0e1305d692a71c28609c80bf0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-standalone-r-server"></a>Créer un serveur R autonome

Le programme d’installation de SQL Server inclut la possibilité d’installer un serveur qui s’exécute en dehors de SQL Server d’apprentissage. 

Cette option peut être utile si vous avez besoin développer des solutions R hautes performances sur Windows, puis partager les solutions sur d’autres plateformes. Vous pouvez également utiliser l’option de serveur pour configurer un environnement de création de solutions pour la prise en charge de l’exécution de ces contextes de calcul à distance :
  
  + Une instance de SQL Server exécutant R Services
  + Une instance de R Server utilisant un cluster Hadoop ou Spark
  + Analyse dans la base de données Teradata
  + R Server s’exécutant dans Linux 

Cette rubrique décrit les étapes d’installation dans le programme d’installation de SQL Server pour Microsoft R Server et Microsoft Machine Learning Server.

## <a name="which-should-i-install"></a>Laquelle dois-je installer ?

**Microsoft R Server** proposé pour la première fois dans le cadre de SQL Server 2016 et prend en charge le langage R. La dernière version de Microsoft R Server a été 9.0.1.
Dans SQL Server 2017, R Server a été renommé **Microsoft Machine Learning Server**, avec prise en charge pour Python. La dernière version du serveur de Microsoft Machine Learning est 9.1.0.

Microsoft R Server et nécessitent tous deux Microsoft Machine Learning Server Enterprise Edition.

+ [Installer Microsoft R Server (autonome) à l’aide du programme d’installation de SQL Server](#bkmk_installRServer)
+ [Installez Microsoft Machine Learning Server (autonome) à l’aide du programme d’installation de SQL Server](#bkmk_installRServer) 

  Le programme d’installation nécessite une licence SQL Server et les mises à niveau suivent généralement la cadence de publication de SQL Server. Vous avez ainsi assuré que vos outils de développement sont en phase avec la version s’exécutant dans le contexte de calcul de SQL Server.

+ [Installer R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)

  Avec cette option, R Server est installé à l’aide de la stratégie de prise en charge du cycle de vie moderne. Vous pouvez également exécuter ce programme d’installation après l’installation pour mettre à niveau une instance de SQL Server 2016. Actuellement, vous _ne peut pas_ installer Python prennent en charge à l’aide de cette option. Pour obtenir les Python, vous devez installer le serveur d’apprentissage Machine à l’aide du programme d’installation de SQL Server 2017.

##  <a name="bkmk_installRServer"></a>L’installation de Microsoft d’apprentissage automatique Server (autonome)
  
1. Si vous avez installé une version antérieure de Microsoft R Server, nous vous recommandons de désinstaller tout d’abord.

2. Exécutez le programme d’installation de SQL Server 2017.
  
3. Cliquez sur le **Installation** et sélectionnez **installation de la nouvelle Machine Learning Server (autonome)**.

4. Une fois la vérification des règles terminée, acceptez les termes du contrat de licence de SQL Server et sélectionnez une nouvelle installation.

5. Sur le **sélection des fonctionnalités** page, ce qui suit options doivent déjà être sélectionnées :
    
    - Microsoft Machine Learning Server (autonome)
    
    - R et Python est sélectionnées par défaut.
    
    Toutes les autres options peuvent être ignorées.

6.  Accepter les termes du contrat de licence pour télécharger et installer les composants d’apprentissage automatique. Un contrat de licence distinct est requis pour Microsoft R Open et Python. 
    
    Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 
    
    L’installation de ces composants (et des autres composants éventuellement requis) peut prendre un certain temps. 
    
    Si l’ordinateur n’a pas accès à Internet, vous devez télécharger les programmes d’installation du composant à l’avance. Pour plus d’informations, consultez [composants ML d’installation sans accès à Internet](./installing-ml-components-without-internet-access.md). 
    
7.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.


Pour plus d’informations sur l’installation automatisée ou hors connexion, consultez [Installer Microsoft R Server à partir de la ligne de commande](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md).

###  <a name="bkmk_installRServer"></a> Installer Microsoft R Server (autonome)  

1. Si vous avez installé une version précédente de Microsoft R Server, ou n’importe quelle version des outils Revolution Analytique, vous devez le désinstaller tout d’abord.  Consultez [Mise à niveau depuis une version antérieure de Microsoft R Server](#bkmk_Uninstall).

2. Exécutez le programme d’installation de SQL Server 2016. Nous vous recommandons d’installer Service Pack 1 ou version ultérieure.

3. Dans l’onglet **Installation** , cliquez sur **Nouvelle installation de R Server (autonome)** .
    
     ![Option d’installation de R Serveur (autonome)](media/rsql-rstandalonesetup.png "Option d’installation de R Server (autonome)")
    
4.  Dans la page **Sélection de fonctionnalités** , l’option suivante doit déjà être sélectionnée :
    
    **R Server (autonome)**  
    
    Toutes les autres options peuvent être ignorées. N’installez pas le moteur de base de données SQL Server ou SQL Server R Services.
    
5.  Acceptez les termes du contrat de licence pour télécharger et installer Microsoft R Open. Lorsque le bouton **Accepter** n’est plus disponible, vous pouvez cliquer sur **Suivant**. 
    
    L’installation de ces composants (et des autres composants éventuellement requis) peut prendre un certain temps.
    
6.  Sur la page **Prêt pour l’installation** , vérifiez vos sélections, et cliquez sur **Installer**.  


### <a name="upgrade-an-existing-r-server-to-901"></a>Mettre à niveau un serveur existant de R à 9.0.1

Si vous avez installé une version antérieure de Microsoft R Server (autonome), vous pouvez mettre à niveau l’instance pour utiliser les dernières versions des composants R. La mise à niveau modifie également le serveur de stratégie de prise en charge du cycle de vie moderne. Cela permet à l’instance mise à jour plus fréquemment, sur une autre planification de mises à jour de SQL Server.

1. Installez Microsoft R Server (autonome), si ce n’est pas déjà fait.

2. Téléchargement de l’installateur basé sur Windows distinct à partir des emplacements répertorié ici : [exécuter Microsoft R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#howtoinstall).

3. Exécutez le programme d’installation et suivez [ces instructions](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#download-r-server-installer).


### <a name="change-in-default-folder-for-r-packages"></a>Modifier les dossiers par défaut pour les Packages R

Lorsque vous installez à l’aide du programme d’installation de SQL Server, les bibliothèques R sont installés dans un dossier associé à la version de SQL Server que vous avez utilisé pour le programme d’installation. Dans ce dossier, vous trouverez aussi des exemples de données, la documentation relative aux packages de base R, ainsi que celle portant sur les outils et le runtime R.

**R Server (autonome) avec une installation basée sur SQL Server 2016**

`C:\Program Files\Microsoft SQL Server\130\R_SERVER`

**R Server (autonome) avec une installation basée sur SQL Server 2017**

`C:\Program Files\Microsoft SQL Server\140\R_SERVER`

**Le programme d’installation à l’aide du programme d’installation autonome de Windows**

Toutefois, si vous installez à l’aide du programme d’installation Windows distinct, ou si vous mettez à niveau à l’aide du programme d’installation Windows distinct, les bibliothèques R sont déplacés dans le dossier R Server suivant :

`C:\Program Files\Microsoft\R Server\R_SERVER`
      
**Le programme d’installation de R services ou d’apprentissage automatique des Services de bases de données**

Si vous avez installé une instance de SQL Server avec R Services (de-de base de données) ou Machine Learning (de-de base de données), et cette instance est sur le même ordinateur, les bibliothèques R et les outils sont installés par défaut dans un dossier différent :

`C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`

N’appelez pas directement les packages ou les utilitaires R associés à l’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Si le serveur R et R Services sont installés sur le même ordinateur, lorsque vous devez exécuter RGui ou autres outils, utilisez les outils R et les packages installés dans le dossier R_SERVER.


### <a name="development-tools"></a>Outils de développement

Un développement IDE n’est pas installé dans le cadre du programme d’installation. Des outils supplémentaires ne sont pas requis, comme tous les outils standards sont inclus qui serait fournie avec une distribution de R ou Python.

Nous vous recommandons la la nouvelle version de [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], comme Visual Studio prend en charge les outils R et Python, ainsi que SQL Server et BI. Toutefois, vous pouvez utiliser n’importe quel environnement de développement par défaut, y compris RStudio.

## <a name="troubleshooting"></a>Dépannage  

### <a name="incompatible-version-of-r-client-and-r-server"></a>Version incompatible de R Client et de R Server

Si vous installez la dernière version de Microsoft R Client et l’utilisez pour exécuter R sur SQL Server à l’aide d’un contexte de calcul distant, il est possible que vous obteniez l’erreur suivante :

*Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

En règle générale, la version de R installée avec SQL Server R Services est mise à jour lors de la publication des versions de service. Pour vous assurer que vous disposez toujours des versions les plus récentes des composants R, installez tous les Service Packs. Pour la compatibilité avec Microsoft R Client 9.0.0, vous devez installer les mises à jour qui sont décrites dans cet [article de support](https://support.microsoft.com/kb/3210262). 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Installation de Microsoft R Server sur une instance de SQL Server installée sur Windows Core

Dans la version RTM de SQL Server 2016, il a été un problème connu lors de l’ajout de Microsoft R Server pour une instance sur l’édition de Windows Server Core. Ce problème a été résolu.

Si vous rencontrez ce problème, vous pouvez appliquer le correctif décrit dans [KB3164398](https://support.microsoft.com/kb/3164398) pour ajouter la fonctionnalité R à l’instance existante sur Windows Server Core.   Pour plus d’informations, consultez [Impossible d’installation Microsoft R Server (autonome) sur un système d’exploitation Windows Server Core](https://support.microsoft.com/kb/3168691).


###  <a name="bkmk_Uninstall"></a> Mise à niveau depuis une version antérieure de Microsoft R Server

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

[Microsoft R Server](../../advanced-analytics/r-services/r-server-standalone.md)


