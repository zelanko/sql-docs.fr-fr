---
title: FAQ (Forum aux questions) sur la mise à niveau et l’installation
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: davidph
author: dphansen
ms.openlocfilehash: 0ee8902dad88cc148481585aaa9e1e083e536d0f
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469898"
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning-or-r-server"></a>FAQ sur la mise à niveau et l’installation de SQL Server Machine Learning ou R Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette rubrique fournit des réponses à certaines questions courantes sur l’installation des fonctionnalités de Machine Learning dans SQL Server. Elle traite également des questions courantes sur les mises à niveau.

+ Certains problèmes se produisent uniquement avec les mises à niveau des versions préliminaires. Par conséquent, nous vous recommandons d’identifier votre version et votre édition avant de lire ces notes. Pour obtenir des informations sur la `@@VERSION` version, exécutez dans une requête à partir de SQL Server Management Studio.
+ Effectuez une mise à niveau vers la version la plus récente ou la version du service le plus rapidement possible pour résoudre les problèmes résolus dans les versions récentes.

**S’applique à :** SQL Server 2016 R services, SQL Server 2017 Machine Learning Services (en base de données)

## <a name="requirements-and-restrictions-on-older-versions-of-sql-server-2016"></a>Exigences et restrictions sur les versions antérieures de SQL Server 2016 

Selon la génération de SQL Server que vous installez, certaines des limitations suivantes peuvent s’appliquer:

- Dans les versions antérieures de SQL Server 2016 R services, la notation 8dot3 était requise sur le lecteur qui contient le répertoire de travail. Si vous avez installé une version préliminaire, la mise à niveau vers SQL Server 2016 Service Pack 1 devrait résoudre ce problème. Cette exigence ne s’applique pas aux mises en production après SP1.

- Actuellement, vous ne pouvez [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] pas installer sur un cluster de basculement. Toutefois, SQL Server 2019 Preview offre une prise en charge du basculement si vous souhaitez évaluer cette fonctionnalité dans un environnement de test. Pour plus d’informations, consultez [Nouveautés](../what-s-new-in-sql-server-machine-learning-services.md).

- Sur une machine virtuelle Azure, une configuration supplémentaire peut être nécessaire. Par exemple, vous devrez peut-être créer une exception de pare-feu pour prendre en charge l’accès à distance.

- L’installation côte à côte avec une autre version de R, ou avec d’autres versions de Revolution Analytics, n’est pas prise en charge.

- Désactivez l’analyse antivirus avant de commencer l’installation. Une fois l’installation terminée, nous vous recommandons de suspendre l’analyse antivirus sur les [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]dossiers utilisés par. De préférence, interrompez l’analyse [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] sur l’ensemble de l’arborescence.

 - Installation de Microsoft R Server sur une instance de SQL Server installée sur Windows Core. Dans la version RTM de SQL Server 2016, il y avait un problème connu lors de l’ajout de Microsoft R Server à une instance sur l’édition Windows Server Core. Ce problème a été résolu. Si vous rencontrez ce problème, vous pouvez appliquer le correctif décrit dans [KB3164398](https://support.microsoft.com/kb/3164398) pour ajouter la fonctionnalité R à l’instance existante sur Windows Server Core. Pour plus d’informations, consultez [Impossible d’installation Microsoft R Server (autonome) sur un système d’exploitation Windows Server Core](https://support.microsoft.com/kb/3168691).


## <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server-2016"></a>Installation hors connexion de composants Machine Learning pour une version localisée de SQL Server 2016

Les versions préliminaires de SQL Server 2016 n’ont pas réussi à installer les fichiers. cab spécifiques aux paramètres régionaux lors de l’installation hors connexion sans connexion Internet. Ce problème a été résolu dans les versions ultérieures, mais si le programme d’installation renvoie un message indiquant qu’il ne peut pas installer la langue correcte, vous pouvez modifier le nom de fichier pour permettre au programme d’installation de continuer.

+ Modifiez manuellement le fichier du programme d’installation pour vous assurer que la langue correcte est installée. Par exemple, pour installer la version japonaise de SQL Server, vous devez modifier le nom du fichier de SRS_ 8.0.3.0 _**1033**. cab en srs_ 8.0.3.0 _**1041**. cab.
+ L’identificateur de langue utilisé pour les composants Machine Learning doit être le même que la langue d’installation SQL Server ou vous ne pouvez pas terminer l’installation.

## <a name="pre-release-versions-support-policies-upgrade-and-known-issues"></a>Versions préliminaires: prendre en charge les stratégies, les mises à niveau et les problèmes connus

Les nouvelles installations de n’importe quelle version préliminaire [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] de ne sont plus prises en charge. Si vous utilisez une version préliminaire, effectuez une mise à niveau dès que possible.

Cette section contient des instructions détaillées pour des scénarios de mise à niveau spécifiques.

### <a name="how-to-upgrade-sql-server"></a>Procédure de mise à niveau de SQL Server

Vous pouvez mettre à niveau votre version de SQL Server en exécutant à nouveau l’Assistant installation.

+ [Mise à niveau vers SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Mettre à niveau SQL Server à l’aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

Vous pouvez mettre à niveau uniquement les composants Machine Learning à l’aide d’un processus appelé liaison: 
+ [Utiliser SqlBindR pour mettre à niveau les composants Machine Learning](../install/upgrade-r-and-python.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Fin de la prise en charge des mises à niveau sur place à partir des versions préliminaires

Les mises à niveau à partir des versions préliminaires de SQL Server 2016 ne sont plus prises en charge. Cela comprend SQL Server 2016 CTP3, CTP 3.1, CTP 3.2, RC0 ou RC1.

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

Si vous avez des doutes sur la version que vous utilisez, exécutez `@@VERSION` dans une requête à partir de SQL Server Management Studio.

En général, le processus de mise à niveau est le suivant:

1. Sauvegardez les scripts et les données.
2. Désinstallez la version préliminaire.
3. Installez une version Release.

La désinstallation d’une version précommerciale des composants Machine Learning SQL Server peut être complexe et nécessiter l’exécution d’un script spécial. Contactez le support technique pour obtenir de l'aide.

###  <a name="bkmk_Uninstall"></a>Désinstallez avant de procéder à la mise à niveau à partir d’une version antérieure de Microsoft R Server

Si vous avez installé une version préliminaire de Microsoft R Server, commencez par la désinstaller avant de pouvoir mettre à niveau vers une version plus récente.

1.  Dans le **Panneau de configuration**, cliquez sur **Ajout/Suppression de programmes**, et sélectionnez `Microsoft SQL Server 2016 <version number>`.

2.  Dans la boîte de dialogue proposant les options **Ajouter**, **Réparer**ou **Supprimer** les composants, sélectionnez **Supprimer**.
  
3.  Sur la page **Sélectionner les fonctionnalités** sous **Composants partagés**, sélectionnez **R Server (autonome)** . Cliquez sur **Suivant**, puis sur **Terminer** pour désinstaller les composants sélectionnés uniquement.

## <a name="r-services-and-r-server-standalone-side-by-side-errors"></a>Erreurs côte à côte R services et R Server (autonome) 

Dans les versions antérieures de SQL Server 2016, l’installation de R Server (autonome) et de R services (en base de données) en même temps entraînait parfois l’échec de l’installation avec un message «accès refusé». Ce problème a été résolu dans le Service Pack 1 pour SQL Server 2016.

Si vous avez rencontré cette erreur et devez mettre à niveau ces fonctionnalités, effectuez une installation intégrée de SQL Server 2016 avec SP1. Il existe deux façons de résoudre le problème, qui requièrent la désinstallation et la réinstallation de.

1. Désinstallez R services (dans la base de données) et assurez-vous que les comptes d’utilisateur pour SQLRUserGroup sont supprimés.

2. Redémarrez le serveur, puis réinstallez R Server (autonome).

3. Exécutez le programme d’installation de SQL Server une fois de plus, puis sélectionnez **Ajouter des fonctionnalités aux SQL Server existants**.

4. Choisissez l’instance, puis sélectionnez l’option **R services (en base de données)** à ajouter.

Si cette procédure ne parvient pas à résoudre le problème, essayez la solution de contournement suivante:

1. Désinstallez R services (en base de données) et R Server (autonomes) en même temps.

2. Supprimez les comptes d’utilisateurs locaux (SQLRUserGroup).

3. Redémarrez le serveur.

4. Exécutez le programme d’installation de SQL Server et ajoutez la fonctionnalité R services (en base de données) uniquement. Ne sélectionnez pas **R Server (autonome)** .

En règle générale, nous vous recommandons de ne pas installer à la fois R services (en base de données) et R Server (autonomes) sur le même ordinateur. Toutefois, en supposant que le serveur dispose d’une capacité suffisante, vous pouvez trouver R Server autonome peut être utile en tant qu’outil de développement. Un autre scénario possible est que vous devez utiliser les fonctionnalités de fonctionnement de R Server, mais que vous souhaitez également accéder aux données SQL Server sans déplacement de données.

## <a name="incompatible-version-of-r-client-and-r-server"></a>Version incompatible de R Client et de R Server

Si vous installez Microsoft R Client et que vous l’utilisez pour exécuter R dans un contexte de calcul SQL Server à distance, vous pouvez obtenir une erreur semblable à celle-ci:

*Vous exécutez la version 9.0.0 de Microsoft R client sur votre ordinateur, ce qui est incompatible avec la version de Microsoft R Server 8.0.3. Téléchargez et installez une version compatible.*

Dans SQL Server 2016, il était nécessaire que la version de R qui était exécutée dans SQL Server R Services soit exactement la même que les bibliothèques dans Microsoft R Client. Cette exigence a été supprimée dans les versions ultérieures. Toutefois, nous vous recommandons de toujours récupérer les dernières versions des composants de Machine Learning et d’installer tous les service packs. 

Si vous disposez d’une version antérieure de Microsoft R Server et que vous devez garantir la compatibilité avec Microsoft R Client 9.0.0, installez les mises à jour décrites dans cet [article de support](https://support.microsoft.com/kb/3210262).


## <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>L’installation échoue avec l’erreur : « Seul un produit Revolution Enterprise peut être installé à la fois. »

Vous pouvez rencontrer cette erreur si votre installation de produits Revolution Analytics est ancienne ou si vous disposez d’une version préliminaire de SQL Server R Services. Vous devez désinstaller toute version précédente avant de pouvoir installer une version plus récente de Microsoft R Server. L’installation côte à côte avec d’autres versions des outils Revolution Enterprise n’est pas prise en charge.

Cependant, les installations côte à côte sont prises en charge quand R Server (autonome) est utilisé avec [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] ou SQL Server 2016.

## <a name="registry-cleanup-to-uninstall-older-components"></a>Nettoyage du Registre pour désinstaller les composants plus anciens

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

 [Machine Learning Server SQL Server (autonome)](../r/r-server-standalone.md)
