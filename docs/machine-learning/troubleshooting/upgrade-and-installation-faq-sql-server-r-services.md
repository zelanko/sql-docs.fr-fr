---
title: FAQ sur l’installation et la mise à niveau
description: La réponse à certaines questions courantes sur l’installation et la mise à niveau des fonctionnalités de Machine Learning de SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/06/2019
ms.topic: troubleshooting
ms.author: davidph
author: dphansen
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cd0c92ef777c87f7d272d229d6e947eb16c9fd7d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87253663"
---
# <a name="installation-and-upgrade-faq-for-sql-server-machine-learning-or-r-server"></a>FAQ sur l’installation et la mise à niveau de SQL Server Machine Learning ou R Server
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Cet article apporte la réponse à certaines questions courantes sur l’installation des fonctionnalités de Machine Learning de SQL Server. Elle traite également des questions courantes sur les mises à niveau.

+ Certains problèmes se produisent uniquement lors des mises à niveau des préversions. Par conséquent, nous vous recommandons d’identifier votre version et votre édition avant de lire ces notes. Pour obtenir des informations sur la version, exécutez `@@VERSION` dans une requête à partir de SQL Server Management Studio.
+ Effectuez une mise à niveau vers la version la plus récente ou la version du service dès que possible pour résoudre les problèmes résolus dans les versions récentes.

**S’applique à :** SQL Server 2016 R Services, SQL Server Machine Learning Services (dans la base de données)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>Exigences et restrictions sur les versions antérieures de SQL Server 2016 

Selon la génération de SQL Server que vous installez, certaines des restrictions suivantes peuvent s’appliquer :

- Dans les versions antérieures de SQL Server 2016 R Services, la notation 8dot3 était requise sur le lecteur qui contient le répertoire de travail. Si vous avez installé une préversion, la mise à niveau vers SQL Server 2016 Service Pack 1 devrait résoudre ce problème. Cette exigence ne s’applique pas aux mises en production ultérieures à SP1.

- Vous ne pouvez pas installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un cluster de basculement dans SQL Server 2016. Cependant, SQL Server 2019 assure la prise en charge du basculement. Pour plus d’informations, voir [Nouveautés](../what-s-new-in-sql-server-machine-learning-services.md).

- Sur une machine virtuelle Azure, une configuration supplémentaire peut être nécessaire. Par exemple, vous devrez peut-être créer une exception de pare-feu pour prendre en charge l’accès à distance.

- L’installation côte à côte en utilisant une autre version de R ou d’autres versions de Revolution Analytics n’est pas prise en charge.

- Désactivez l’analyse antivirus avant de commencer l’installation. Une fois l’installation terminée, nous vous recommandons de suspendre l’analyse antivirus sur les dossiers utilisés par [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]. De préférence, interrompez l’analyse sur l’ensemble de l’arborescence [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].

 - Installation de Microsoft R Server sur une instance SQL Server installée sur Windows Core. Dans la version RTM de SQL Server 2016, il y avait un problème connu lors de l’ajout de Microsoft R Server à une instance sur l’édition Windows Server Core. Ce problème a été résolu. Si vous rencontrez ce problème, vous pouvez appliquer le correctif décrit dans [KB3164398](https://support.microsoft.com/kb/3164398) pour ajouter la fonctionnalité R à l’instance existante sur Windows Server Core. Pour plus d’informations, consultez [Impossible d’installation Microsoft R Server (autonome) sur un système d’exploitation Windows Server Core](https://support.microsoft.com/kb/3168691).


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>Installation hors connexion des composants Machine Learning pour la version localisée de SQL Server 2016

Les préversions de SQL Server 2016 n’ont pas réussi à installer les fichiers. cab spécifiques des paramètres régionaux lors de l’installation hors connexion sans connexion Internet. Ce problème a été résolu dans les versions ultérieures. Toutefois, si le programme d’installation renvoie un message indiquant qu’il ne peut pas installer la langue correcte, vous pouvez modifier le nom de fichier pour permettre au programme d’installation de continuer.

+ Modifiez manuellement le fichier du programme d’installation pour vous assurer que la langue correcte est installée. Par exemple, pour installer la version japonaise de SQL Server, remplacez le nom du fichier SRS_8.0.3.0_**1033**.cab par SRS_8.0.3.0_**1041**.cab.
+ L’identificateur de langue utilisé pour les composants Machine Learning doit être le même que la langue de configuration de SQL Server, sinon vous ne pouvez pas terminer la configuration.

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>Préversions : stratégies de pris en charge, mise à niveau et problèmes connus

Les nouvelles installations de préversions de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ne sont plus prises en charge. Si vous utilisez une préversion, effectuez une mise à niveau dès que possible.

Cette section contient des instructions détaillées pour des scénarios de mise à niveau spécifiques.

### <a name="how-to-upgrade-sql-server"></a>Mise à niveau de SQL Server

Vous pouvez effectuer une mise à niveau de votre version de SQL Server en réexécutant l’Assistant Installation.

+ [Mise à niveau vers SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Effectuer une mise à niveau de SQL Server à l’aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Vous pouvez mettre à niveau uniquement les composants Machine Learning à l’aide d’un processus appelé « liaison » : 
+ [Utiliser SqlBindR pour mettre à niveau les composants Machine Learning](../install/upgrade-r-and-python.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Fin de la prise en charge des mises à niveau sur place à partir des préversions

Les mises à niveau à partir des préversions de SQL Server 2016 ne sont plus prises en charge. Cela comprend SQL Server 2016 CTP3, CTP3.1, CTP3.2, RC0 ou RC1.

Les versions suivantes ont été installées avec les préversions de SQL Server 2016.

| Version | Build         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Si vous avez des doutes sur la version que vous utilisez, exécutez `@@VERSION` dans une requête à partir de SQL Server Management Studio.

En général, le processus de mise à niveau est le suivant :

1. Sauvegardez les scripts et les données.
2. Désinstallez la préversion.
3. Installez une préversion.

La désinstallation d’une préversion des composants SQL Server Machine Learning SQL Server peut être complexe et nécessiter l’exécution d’un script spécial. Contactez le support technique pour obtenir de l'aide.

###  <a name="uninstall-prior-to-upgrading-from-an-older-version-of-microsoft-r-server"></a><a name="bkmk_Uninstall"></a> Désinstallation avant la mise à niveau depuis une version antérieure de Microsoft R Server

Si vous avez installé une version préliminaire de Microsoft R Server, commencez par la désinstaller avant de pouvoir mettre à niveau vers une version plus récente.

1.  Dans le **Panneau de configuration**, cliquez sur **Ajout/Suppression de programmes**, et sélectionnez `Microsoft SQL Server 2016 <version number>`.

2.  Dans la boîte de dialogue proposant les options **Ajouter**, **Réparer**ou **Supprimer** les composants, sélectionnez **Supprimer**.
  
3.  Sur la page **Sélectionner les fonctionnalités** sous **Composants partagés**, sélectionnez **R Server (autonome)** . Cliquez sur **Suivant**, puis sur **Terminer** pour désinstaller les composants sélectionnés uniquement.

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>Erreurs côte à côte de R services et R Server (autonome) 

Dans les versions antérieures de SQL Server 2016, l’installation simultanée de R Server (autonome) et de R services (dans la base de données) entraînait parfois l’échec de l’installation accompagné d’un message « accès refusé ». Ce problème a été résolu dans le Service Pack 1 pour SQL Server 2016.

Si vous avez rencontré cette erreur et devez mettre à niveau ces fonctionnalités, effectuez une installation intégrée de SQL Server 2016 avec SP1. Il existe deux façons de résoudre le problème, qui requièrent toutes deux une désinstallation et une réinstallation.

1. Désinstallez R services (dans la base de données) et assurez-vous que les comptes d’utilisateur pour SQLRUserGroup sont supprimés.

2. Redémarrez le serveur, puis réinstallez R Server (autonome).

3. Exécutez de nouveau le programme d’installation SQL Server, puis sélectionnez cette fois **Ajouter des fonctionnalités au SQL Server existant**.

4. Choisissez l’instance, puis sélectionnez l’option **R services (dans la base de données)** à ajouter.

Si cette procédure ne parvient pas à résoudre le problème, essayez la solution de contournement suivante :

1. Désinstallez simultanément R Services (dans la base de données) et R Server (autonome).

2. Supprimez les comptes d’utilisateurs locaux (SQLRUserGroup).

3. Redémarrez le serveur.

4. Exécutez le programme d’installation de SQL Server et ajoutez la fonctionnalité R services (dans la base de données) uniquement. Ne sélectionnez pas **Microsoft R Server (autonome)** .

En règle générale, nous vous recommandons de ne pas installer à la fois R services (dans la base de données) et R Server (autonome) sur le même ordinateur. Toutefois, en supposant que le serveur dispose d’une capacité suffisante, R Server (autonome) est susceptible d’être utile en tant qu’outil de développement. Un autre scénario possible est d’avoir besoin d’utiliser les fonctionnalités de fonctionnement de R Server, tout en voulant également accéder aux données SQL Server sans déplacer de données.

## <a name="incompatible-version-of-r-client-and-r-server"></a>Version incompatible de R Client et de R Server

Si vous installez Microsoft R Client et que vous vous en servez pour exécuter R sur SQL Server dans un contexte de calcul distant, il est possible que vous obteniez une erreur de ce type :

*Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

Dans SQL Server 2016, il était nécessaire que la version de R qui était exécutée dans SQL Server R Services soit exactement la même que celle des bibliothèques dans Microsoft R Client. Cette exigence a été supprimée dans les versions ultérieures. Toutefois, nous vous recommandons de toujours récupérer les dernières versions des composants de Machine Learning et d’installer tous les Service Packs. 

Si vous disposez d’une ancienne version de Microsoft R Server Pour assurer la compatibilité avec Microsoft R Client 9.0.0, installez les mises à jour qui sont décrites dans cet [article de support](https://support.microsoft.com/kb/3210262).


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L’installation échoue avec l’erreur : « Seul un produit Revolution Enterprise peut être installé à la fois. »

Vous pouvez rencontrer cette erreur si votre installation de produits Revolution Analytics est ancienne ou si vous disposez d’une version préliminaire de SQL Server R Services. Vous devez désinstaller toute version précédente avant de pouvoir installer une version plus récente de Microsoft R Server. L’installation côte à côte avec d’autres versions des outils Revolution Enterprise n’est pas prise en charge.

Cependant, les installations côte à côte sont prises en charge quand R Server (autonome) est utilisé avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] ou SQL Server 2016.

## <a name="registry-cleanup-to-uninstall-older-components"></a>Nettoyage du registre pour désinstaller les composants plus anciens

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

 [SQL Server Machine Learning Services (dans la base de données)](../r/sql-server-r-services.md)

 [SQL Server Machine Learning Server (autonome)](../r/r-server-standalone.md)
