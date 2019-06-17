---
title: Mise à niveau et installation Forum aux questions (FAQ) - SQL Server Machine Learning Services
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: davidph
author: dphansen
manager: cgronlun
ms.openlocfilehash: 8a53069195ee351630f2ef79f56069f013137d9b
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140366"
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>FAQ d’installation et de mise à niveau pour SQL Server Machine Learning ou R Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette rubrique fournit des réponses aux questions courantes sur l’installation de fonctionnalités dans SQL Server d’apprentissage. Il couvre également les questions courantes sur les mises à niveau.

+ Certains problèmes se produisent uniquement avec les mises à niveau à partir de versions préliminaires. Par conséquent, nous vous recommandons d’identifier votre version et l’édition tout d’abord avant de lire ces notes de publication. Pour obtenir des informations de version, exécutez `@@VERSION` dans une requête à partir de SQL Server Management Studio.
+ Mettre à niveau vers la version la plus récente ou d’une version de service dès que possible pour résoudre les problèmes qui ont été résolus dans les versions récentes.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services (en base de données)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>Exigences et restrictions sur les versions antérieures de SQL Server 2016 

Selon la version de SQL Server que vous installez, certaines des limitations suivantes peuvent s’appliquer :

- Dans les versions antérieures de SQL Server 2016 R Services, la notation 8dot3 était nécessaire sur le lecteur qui contient le répertoire de travail. Si vous avez installé une version préliminaire, la mise à niveau vers SQL Server 2016 Service Pack 1 doit résoudre ce problème. Cette exigence ne s’applique pas aux versions après SP1.

- Actuellement, vous ne pouvez pas installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un cluster de basculement. Toutefois, les version préliminaire de SQL Server 2019 ne prend en charge de basculement si vous souhaitez évaluer cette fonctionnalité dans un environnement de test. Pour plus d’informations, consultez [What ' s New](../what-s-new-in-sql-server-machine-learning-services.md).

- Sur une machine virtuelle Azure, une configuration supplémentaire peut être nécessaire. Par exemple, vous devrez peut-être créer une exception de pare-feu pour prendre en charge l’accès à distance.

- Installation côte à côte avec une autre version de R, ou avec d’autres versions de Revolution Analytique, n’est pas pris en charge.

- Désactiver l’analyse antivirus, avant de commencer l’installation. Une fois le programme d’installation est terminée, nous vous recommandons d’interrompre l’analyse antivirus sur les dossiers utilisés par [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]. De préférence, suspendre l’analyse de l’ensemble [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] arborescence.

 - Installez Microsoft R Server sur une instance de SQL Server installée sur Windows Core. Dans la version RTM de SQL Server 2016, il y avait un problème connu lors de l’ajout de Microsoft R Server à une instance sur l’édition Windows Server Core. Ce problème a été résolu. Si vous rencontrez ce problème, vous pouvez appliquer le correctif décrit dans [KB3164398](https://support.microsoft.com/kb/3164398) pour ajouter la fonctionnalité R à l’instance existante sur Windows Server Core. Pour plus d’informations, consultez [Impossible d’installation Microsoft R Server (autonome) sur un système d’exploitation Windows Server Core](https://support.microsoft.com/kb/3168691).


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>Installation hors connexion de composants d’apprentissage automatique pour une version localisée de SQL Server 2016

Échec de la libération anticipée des versions de SQL Server 2016 à installer les fichiers .cab de paramètres régionaux spécifiques lors de l’installation hors connexion sans connexion internet. Ce problème a été résolu dans les versions ultérieures, mais si le programme d’installation renvoie un message indiquant qu’il ne peut pas installer la langue appropriée, vous pouvez modifier le nom de fichier pour que l’installation puisse continuer.

+ Modifier manuellement le fichier de programme d’installation pour vous assurer que la langue correcte est installée. Par exemple, pour installer la version japonaise de SQL Server, vous remplacerez le nom du fichier srs_8.0.3.0_**1033**.cab par SRS_8.0.3.0_**1041**.cab.
+ L’identificateur de langue utilisé pour les composants d’apprentissage doit être identique à la langue d’installation de SQL Server, ou vous ne pouvez pas terminer le programme d’installation.

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>Versions préliminaires : prend en charge les stratégies de mise à niveau et problèmes connus

Les nouvelles installations de n’importe quelle version de la version préliminaire de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] n’est plus pris en charge. Si vous utilisez une version préliminaire, mettez à niveau dès que possible.

Cette section contient des instructions détaillées pour les scénarios de mise à niveau spécifiques.

### <a name="how-to-upgrade-sql-server"></a>Comment mettre à niveau de SQL Server

Vous pouvez mettre à niveau votre version de SQL Server en réexécutant l’Assistant installation.

+ [Mise à niveau vers SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Mise à niveau SQL Server à l’aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Vous pouvez mettre à niveau seulement pour la machine learning de composants à l’aide d’un processus appelé liaison : 
+ [Utiliser SqlBindR pour mettre à niveau les composants d’apprentissage automatique](../install/upgrade-r-and-python.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Fin de prise en charge des mises à niveau sur place à partir de versions préliminaires

Mises à niveau à partir de versions préliminaires de SQL Server 2016 ne sont plus prises en charge. Cela inclut SQL Server 2016 CTP3, CTP3.1, CTP3.2, RC0 ou RC1.

Les versions suivantes ont été installées avec les versions préliminaires de SQL Server 2016.

| Version | Build         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Si vous avez un doute sur la version que vous utilisez, exécutez `@@VERSION` dans une requête à partir de SQL Server Management Studio.

En règle générale, le processus de mise à niveau est la suivante :

1. Sauvegardez les scripts et les données.
2. Désinstallez la version préliminaire.
3. Installer une version release.

Désinstallation d’une version préliminaire de SQL Server les composants d’apprentissage automatique peuvent être complexes et peut nécessiter l’exécution d’un script spécial. Contactez le support technique pour obtenir de l'aide.

###  <a name="bkmk_Uninstall"></a> Désinstallez avant la mise à niveau à partir d’une version antérieure de Microsoft R Server

Si vous avez installé une version préliminaire de Microsoft R Server, commencez par la désinstaller avant de pouvoir mettre à niveau vers une version plus récente.

1.  Dans le **Panneau de configuration**, cliquez sur **Ajout/Suppression de programmes**, et sélectionnez `Microsoft SQL Server 2016 <version number>`.

2.  Dans la boîte de dialogue proposant les options **Ajouter**, **Réparer**ou **Supprimer** les composants, sélectionnez **Supprimer**.
  
3.  Sur la page **Sélectionner les fonctionnalités** sous **Composants partagés**, sélectionnez **R Server (autonome)** . Cliquez sur **Suivant**, puis sur **Terminer** pour désinstaller les composants sélectionnés uniquement.

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>R Services et les erreurs de côte à côte de R Server (autonome) 

Dans les versions antérieures de SQL Server 2016, l’installation de R Server (autonome) et R Services (en base de données) en même temps parfois dû le programme d’installation échoue avec un message « accès refusé ». Ce problème a été résolu dans le Service Pack 1 pour SQL Server 2016.

Si vous cette erreur s’est produite et que vous devez mettre à niveau ces fonctionnalités, effectuez une installation intégrée de SQL Server 2016 avec SP1. Il existe deux façons pour résoudre le problème, les deux devoir désinstaller puis réinstaller.

1. Désinstallez R Services (en base de données) et assurez-vous que les comptes d’utilisateurs SQLRUserGroup sont supprimés.

2. Redémarrez le serveur, et réinstallez R Server (autonome).

3. Exécuter SQL Server le programme d’installation une fois plus d’informations, et cette fois-ci, sélectionnez **ajouter des fonctionnalités à un serveur SQL existant**.

4. Choisissez l’instance, puis sélectionnez le **R Services (en base de données)** option permettant d’ajouter.

Si cette procédure ne parvient pas à résoudre le problème, essayez la solution de contournement suivante :

1. Désinstallez R Services (en base de données) et R Server (autonome) en même temps.

2. Supprimer les comptes d’utilisateur local (SQLRUserGroup).

3. Redémarrez le serveur.

4. Exécutez le programme d’installation de SQL Server et ajouter la fonctionnalité R Services (en base de données) uniquement. Ne sélectionnez pas **R Server (autonome)** .

En règle générale, nous vous recommandons de ne pas installer R Services (en base de données) et R Server (autonome) sur le même ordinateur. Toutefois, en supposant que le serveur possède une capacité suffisante, vous constaterez peut-être que r Server autonome peut être utile comme outil de développement. Un autre scénario possible est que vous devez utiliser les fonctionnalités de l’Opérationnalisation de R Server, mais que vous souhaitez également accéder aux données de SQL Server sans déplacement de données.

## <a name="incompatible-version-of-r-client-and-r-server"></a>Version incompatible de R Client et de R Server

Si vous installez Microsoft R Client et l’utiliser pour exécuter R dans un contexte de calcul SQL Server distant, vous pouvez obtenir une erreur comme suit :

*Vous exécutez la version 9.0.0 de Microsoft R client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

Dans SQL Server 2016, il était nécessaire que la version de R qui s’exécutait dans SQL Server R Services être exactement le même que les bibliothèques Microsoft R Client. Cette exigence a été supprimée dans les versions ultérieures. Toutefois, nous recommandons que vous toujours obtenez les dernières versions des composants d’apprentissage et installez tous les service packs. 

Si vous avez une version antérieure de Microsoft R Server et que vous avez besoin assurer la compatibilité avec la version 9.0.0 de Microsoft R Client, installez les mises à jour qui sont décrites dans ce [article du support technique](https://support.microsoft.com/kb/3210262).


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L’installation échoue avec l’erreur : « Seul un produit Revolution Enterprise peut être installé à la fois. »

Vous pouvez rencontrer cette erreur si votre installation de produits Revolution Analytics est ancienne ou si vous disposez d’une version préliminaire de SQL Server R Services. Vous devez désinstaller toute version précédente avant de pouvoir installer une version plus récente de Microsoft R Server. L’installation côte à côte avec d’autres versions des outils Revolution Enterprise n’est pas prise en charge.

Cependant, les installations côte à côte sont prises en charge quand R Server (autonome) est utilisé avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] ou SQL Server 2016.

## <a name="registry-cleanup-to-uninstall-older-components"></a>Nettoyage de Registre pour désinstaller les composants plus anciens

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

 [SQL Server Machine Learning Services (en base de données)](../r/sql-server-r-services.md)

 [SQL Server Machine Learning Server (autonome)](../r/r-server-standalone.md)
