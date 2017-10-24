---
title: "Mettre à niveau les composants de la machine learning dans une instance de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 10/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016 CTP3)
ms.assetid: 4da80998-f929-4fad-a86f-87d09c1a79ef
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 9b2d59d860d72207b196ac60a1db66f09baa1228
ms.contentlocale: fr-fr
ms.lasthandoff: 10/13/2017

---
# <a name="upgrade-machine-learning-components-in-a-sql-server-instance"></a>Mettre à niveau les composants de la machine learning dans une instance de SQL Server

Cet article explique le processus de _liaison_, que vous pouvez utiliser pour mettre à niveau les composants utilisés dans SQL Server d’apprentissage automatique. Le processus de liaison verrouille le serveur dans une cadence de mise à jour basée sur des versions de la Machine Learning Server plutôt que SQL Server.

> [!IMPORTANT]
> Vous n’avez pas besoin d’utiliser ce processus de mise à niveau si vous souhaitez obtenir des mises à niveau dans le cadre de mises à jour de SQL Server. Chaque fois que vous installez un nouveau service pack ou une version de service, machine learning composants sont automatiquement mis à niveau vers la dernière version. Utilisez cette procédure si vous souhaitez mettre à niveau des composants à un rythme plus rapide que vous est offerte par les versions de service SQL Server.

Si à tout moment vous souhaitez arrêter la mise à niveau sur la planification de la Machine Learning Server, vous devez _dissocier_ l’instance, comme décrit dans [cette section](#bkmk_Unbind), désinstaller le serveur d’apprentissage Machine.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="binding-vs-upgrading"></a>Liaison et la mise à niveau

Le processus de mise à niveau les composants d’apprentissage automatique est appelé **liaison**, car il modifie le modèle de prise en charge pour les composants de formation ordinateur SQL Server à utiliser la nouvelle stratégie de cycle de vie de logiciel moderne. 

En règle générale, le basculement vers le nouveau modèle de licence garantit que les chercheurs de données peuvent utiliser toujours la dernière version de R ou Python. Pour plus d’informations sur les conditions de la stratégie de cycle de vie moderne, consultez [chronologie de prise en charge de Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-servicing-support).

> [!NOTE]
> La mise à niveau ne modifie pas le modèle de prise en charge pour la base de données SQL Server et ne change pas la version de SQL Server.

Lorsque vous liez une instance, plusieurs choses se produisent, qui peut inclure une mise à niveau vers les composants d’apprentissage automatique :

+ Le modèle de prise en charge est modifié. Plutôt que sur des versions de service SQL Server, prise en charge est basée sur la nouvelle stratégie de cycle de vie moderne.
+ Les composants d’apprentissage machine associés à l’instance sont automatiquement mis à niveau avec chaque version, dans l’étape de verrou avec la version actuelle sous la nouvelle stratégie de cycle de vie moderne. 
+ Nouveaux packages R ou Python peuvent être ajoutées. Par exemple, précédentes mises à jour à partir de Microsoft R Server ajoutés comme nouveaux packages R, [MicrosoftML](../using-the-microsoftml-package.md), [olapR](../r/how-to-create-mdx-queries-using-olapr.md), et [sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md).
+ L’instance peut ne plus être mise à jour manuellement, excepté pour ajouter de nouveaux packages.
+ Vous avez la possibilité d’ajouter des modèles préformés fournis par Microsoft.

## <a name="bkmk_prereqs"></a>Prérequis

Commencez par identifier les instances qui sont des candidats pour une mise à niveau. Si vous exécutez le programme d’installation et que vous sélectionnez l’option de liaison, il retourne une liste d’instances qui sont compatibles avec la mise à niveau. 

Consultez le tableau suivant pour obtenir la liste des mises à niveau pris en charge et les exigences.

| Version de SQL Server| Mise à niveau pris en charge| Remarques|
|-----|-----|------|
| SQL Server 2016| Serveur 9.2.1 d’apprentissage| Nécessite au moins Service Pack 1 plus CU3. R Services doit être installés et activés.|
| SQL Server 2017| Serveur 9.2.1 d’apprentissage| Machine Learning Services (de-de base de données) doit être installés et activés. |

## <a name="bind-or-upgrade-an-instance"></a>Lier ou mettre à niveau une instance

Microsoft Machine Learning pour Windows Server inclut un outil que vous pouvez utiliser pour mettre à niveau de l’apprentissage de langages et outils associés à une instance de SQL Server. Il existe deux versions de l’outil : un Assistant et un utilitaire de ligne de commande.

Avant de pouvoir exécuter l’Assistant ou l’outil de ligne de commande, vous devez télécharger la dernière version du programme d’installation autonome pour l’apprentissage de composants.

+ [Installer le serveur 9.2.1 d’apprentissage pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ [Télécharger les composants nécessaires à l’installation en mode hors connexion](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)

### <a name="bkmk_BindWizard"></a>Mise à niveau de l’aide du nouvel Assistant d’installation

1. Démarrez le programme d’installation nouveau serveur de Machine Learning. Veillez à exécuter le programme d’installation sur l’ordinateur qui a l’instance que vous souhaitez mettre à niveau.

    ![Assistant Installation du serveur de Microsoft Machine Learning](media/mls-921-installer-start.PNG)

2. Dans la page, **configurer l’installation**, vérifiez les composants à mettre à niveau et passez en revue la liste des instances compatibles. Si aucune instance ne s’affichent, vérifiez le [conditions préalables](#bkmk_prereqs).

    Pour mettre à niveau une instance, sélectionnez la case à cocher en regard du nom d’instance. Si vous ne sélectionnez pas une instance, une installation distincte du serveur de Machine Learning est créée, et les bibliothèques de SQL Server sont identiques.

    ![Assistant Installation du serveur de Microsoft Machine Learning](media/configure-the-installation.PNG)

3. Sur le **contrat de licence** page, sélectionnez **J’accepte les termes** pour accepter les termes du contrat de licence pour l’apprentissage d’ordinateur serveur. 

4. Sur des pages successives, fournir son consentement pour les conditions de licences supplémentaires pour tous les composants open source que vous avez sélectionné, telles que Microsoft R Open ou la distribution de Python Anaconda.

5. Sur le **presque** page, notez le dossier d’installation. Le dossier par défaut est `~\Program Files\Microsoft\ML Server`. 

    Si vous souhaitez modifier le dossier d’installation, cliquez sur **avancé** pour revenir à la première page de l’Assistant. Toutefois, vous devez répéter toutes les sélections précédentes. 

6. Si vous installez les composants en mode hors connexion, vous pouvez être invité pour l’emplacement des composants d’apprentissage nécessaires de l’ordinateur, telles que Microsoft R Open, serveur de Python et ouvrir de Python.
    
Pendant l’installation, toutes les bibliothèques R ou Python utilisés par SQL Server sont remplacés et Launchpad est mis à jour pour utiliser les composants les plus récents. Autrement dit, si l’instance utilisé précédemment des bibliothèques dans le dossier R_SERVICES par défaut, après mise à niveau ces bibliothèques sont supprimés et les propriétés pour le service Launchpad sont modifiées, pour utiliser les bibliothèques dans l’emplacement spécifié.

### <a name="bkmk_BindCmd"></a>Mise à niveau de l’aide de la ligne de commande

Si vous ne souhaitez pas utiliser l’Assistant, vous pouvez installer le serveur de Machine Learning et puis exécutez l’outil SqlBindR.exe à partir de la ligne de commande pour mettre à niveau l’instance.

> [!TIP]
> 
> Impossible de trouver SqlBindR.exe ? Vous avez téléchargé probablement pas les composants répertoriés ci-dessus. Cet utilitaire est disponible uniquement avec le programme d’installation de Windows pour l’apprentissage d’ordinateur serveur.

1. Ouvrez une invite de commandes en tant qu’administrateur et accédez au dossier contenant sqlbindr.exe. L’emplacement par défaut est`C:\Program Files\Microsoft\MLServer\Setup`

2. Tapez la commande suivante pour afficher la liste des instances disponibles : `SqlBindR.exe /list`
  
   Notez le nom complet de l’instance tel qu’il est répertorié. Par exemple, le nom d’instance peut être `MSSQL14.MSSQLSERVER` pour une instance par défaut, ou quelque chose comme `SERVERNAME.MYNAMEDINSTANCE`.

3. Exécutez le **SqlBindR.exe** avec la */lier* argument et spécifiez le nom de l’instance à mettre à niveau, à l’aide du nom de l’instance qui a été retourné à l’étape précédente.

   Par exemple, pour mettre à niveau l’instance par défaut, tapez :`SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Une fois la mise à niveau terminée, redémarrez le service de Launchpad associé à n’importe quelle instance qui a été modifié.

## <a name="bkmk_Unbind"></a>Rétablir ou dissocier une instance

Si vous décidez que vous ne souhaitez plus mettre à niveau les composants à l’aide du serveur d’apprentissage Machine d’apprentissage automatique, vous devez d’abord _dissocier_ l’instance, puis désinstallez le serveur d’apprentissage Machine.

+ Supprimer l’instance de la liaison

    Vous pouvez supprimer l’instance de la liaison et rétablir les bibliothèques d’origine installés par SQL Server, à l’aide d’une des deux méthodes suivantes :

    + [Utilisez l’Assistant Installation](#bkmk_wizunbind) pour serveur de Machine Learning et désélectionnez toutes les fonctionnalités sur l’instance
    + [Utilisez l’utilitaire SqlBindR](#bkmk_cmdunbind) avec la `/unbind` argument, suivi du nom d’instance.

    Lorsque le processus de séparation est terminé, des mises à jour basées sur le serveur d’apprentissage Machine apprentissage futures n’appliquent plus à l’instance.

+ Désinstaller le serveur d’apprentissage

    Pour obtenir des instructions, consultez [désinstaller Machine Learning pour Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-uninstall). 

### <a name="bkmk_wizunbind"></a>Supprimer la liaison à l’aide de l’Assistant

1. Recherchez le programme d’installation pour l’apprentissage d’ordinateur serveur. Si vous avez supprimé le programme d’installation, vous devrez peut-être télécharger à nouveau, ou copiez-la depuis un autre ordinateur.
2. Veillez à exécuter le programme d’installation sur l’ordinateur qui a l’instance que vous souhaitez supprimer la liaison.
2. Le programme d’installation identifie les instances locales qui sont des candidats pour l’annulation de la liaison.
3. Désactivez la case à cocher en regard de l’instance que vous souhaitez revenir à la configuration d’origine.
4. Acceptez le contrat de licence. Vous devez indiquer votre acceptation des termes du contrat de licence même lors de l’installation.
5. Cliquez sur **Terminer**. Le processus prend un certain temps.

### <a name="bkmk_cmdunbind"></a>Supprimer la liaison à l’aide de la ligne de commande

1. Ouvrez une invite de commandes et accédez au dossier qui contient **sqlbindr.exe**, comme décrit dans la section précédente.

2. Exécutez la commande **SqlBindR.exe** avec l’argument */unbind*, puis spécifiez l’instance.

   Par exemple, la commande suivante reprend l’instance par défaut :
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie spécifique de problèmes connus liés à l’aide de l’utilitaire SqlBindR.exe ou aux mises à niveau du serveur Machine Learning susceptibles d’affecter les instances de SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Restauration des packages qui ont été précédemment installées

Dans l’utilitaire de mise à niveau qui a été inclus avec Microsoft R Server 9.0.1, l’utilitaire n’a pas restauré les packages d’origine ou des composants R complètement, demandant à l’utilisateur d’exécuter repair sur l’instance, s’appliquent à toutes les versions de service, puis redémarrez l’instance.

Toutefois, la version la plus récente de l’utilitaire de mise à niveau restaure automatiquement les fonctions R d’origine. Par conséquent, vous ne devez pas à réinstaller les composants de R ou ré-appliquer le correctif. Toutefois, vous devez installer tous les packages R qui ont peut-être été ajoutées après l’installation initiale.

Si vous avez utilisé les rôles de gestion de package à installer et partager le package, cette tâche est beaucoup plus facile : vous pouvez utiliser des commandes R pour synchroniser les packages installés dans le système de fichiers à l’aide d’enregistrements dans la base de données et vice versa. Pour plus d’informations, consultez [gestion des packages R pour SQL Server](r-package-management-for-sql-server-r-services.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Problèmes avec plusieurs mises à niveau à partir de SQL Server

Si vous avez précédemment mis à niveau une instance de SQL Server 2016 R Services à 9.0.1, lorsque vous exécutez le programme d’installation de nouveau pour Microsoft R Server 9.1.0, il affiche une liste de toutes les instances valides, puis sélectionne précédemment liée d’instances par défaut. Si vous continuez, les instances précédemment liés sont indépendants. Par conséquent, la 9.0.1 antérieures installation est supprimée, y compris tous les packages, mais la nouvelle version de Microsoft R Server (9.1.0) n’est pas installée.

Pour résoudre ce problème, vous pouvez modifier l’installation de R Server existante comme suit :
1. Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.
2. Recherchez Microsoft R Server, puis cliquez sur **modification/modifier**.
3. Lorsque le programme d’installation démarre, sélectionnez les instances que vous souhaitez lier à 9.1.0.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>La liaison ou la séparation laisse plusieurs dossiers temporaires

La liaison et annulation de la liaison des opérations échouent parfois à nettoyer les dossiers temporaires.
Si vous trouvez des dossiers avec un nom tel que cela, vous pouvez le supprimer une fois l’installation terminée :`R_SERVICES_<guid>`

> [!NOTE]
> Veillez à attendre que l’installation est terminée. Il peut prendre beaucoup de temps à supprimer les bibliothèques R associé liés une version, puis ajoutez les nouvelles bibliothèques R. Lorsque l’opération est terminée, les dossiers temporaires sont supprimés.

## <a name="sqlbindrexe-command-syntax"></a>Syntaxe de commande sqlbindr.exe

### <a name="usage"></a>Utilisation

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Paramètres

|Nom|Description|
|------|------|
|*list*| Affiche une liste de tous les ID d’instances de bases de données SQL sur l’ordinateur actuel|
|*bind*| Met à niveau l’instance de base de données SQL spécifiée vers la version la plus récente de R Server, et garantit que l’instance obtient automatiquement les mises à niveau ultérieures de R Server|
|*unbind*|Désinstalle la version la plus récente de R Server de l’instance de base de données SQL spécifiée, et empêche les mises à niveau ultérieures de R Server d’affecter l’instance|

### <a name="errors"></a>Erreurs

L’outil retourne les messages d’erreur suivants :

|Erreur|Résolution|
|------|------|
|Une erreur est survenue lors de la liaison de l’instance| L’instance n’a pas pu être liée. Contactez le support pour obtenir de l’aide.|
|L’instance est déjà liée| Vous avez exécuté la commande *bind* , mais l’instance spécifiée est déjà liée. Choisissez une autre instance.|
|L’instance n’est pas liée| Vous avez exécuté la commande *unbind* , mais l’instance que vous avez spécifiée n’est pas liée. Choisissez une autre instance compatible.|
|ID d’instance SQL non valide| Vous avez peut-être mal tapé le nom de l’instance. Exécutez la commande à nouveau à l’aide de l’argument *list* pour voir les ID d’instance disponibles.|
|Aucune instance trouvée| Cet ordinateur ne dispose pas d’une instance de SQL Server R Services.|
|L’instance doit avoir une version compatible de SQL R Services (dans la base de données) installée.| Pour plus d’informations, consultez les spécifications de compatibilité présentées dans cette rubrique.|
|Une erreur est survenue lors de l’annulation de la liaison de l’instance| L’annulation de la liaison de l’instance n’a pas pu être effectuée. Contactez le support pour obtenir de l’aide.|
|Une erreur inattendue s’est produite| Autres erreurs. Contactez le support pour obtenir de l’aide.  |
|Aucune instance SQL trouvée| Cet ordinateur ne dispose pas d’une instance SQL Server. |

Pour plus d’informations, consultez les notes de publication pour Microsoft R Server :

+ [Problèmes connus dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)

+ [Annonces de fonctionnalités à partir de la version précédente de R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)

+ [Fonctionnalités déconseillées, supprimées ou modifiées](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)

