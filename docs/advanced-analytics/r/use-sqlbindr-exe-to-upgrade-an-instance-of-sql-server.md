---
title: "Mettre à niveau les composants de la machine learning dans une instance de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 07/31/2017
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
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9d7ddd95bdbcf6efca98ed94bc305924902b98
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="upgrade-machine-learning-components-in-a-sql-server-instance"></a>Mettre à niveau les composants de la machine learning dans une instance de SQL Server

Microsoft Machine Learning pour Windows Server inclut un outil que vous pouvez utiliser pour mettre à niveau les composants de R associés à une instance de SQL Server. Il existe deux versions de l’outil : un Assistant et un utilitaire de ligne de commande.

Cet article décrit comment utiliser ces outils pour mettre à niveau une instance compatible de SQL Server et comment rétablir une instance précédemment mise à niveau.

Vous n’avez pas besoin d’utiliser ce processus de mise à niveau si vous souhaitez obtenir des mises à niveau dans le cadre de mises à jour de SQL Server. Chaque fois que vous installez un nouveau service pack ou une version de service, machine learning composants sont automatiquement mis à niveau vers la dernière version. Utilisez uniquement cette proess si vous souhaitez mettre à niveau des composants à un rythme plus rapide qu’est affored par les versions de service SQL Server.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

> [!NOTE]
> Au moment de la rédaction, les mises à niveau s’appliquent uniquement aux instances de SQL Server 2016 compatibles.  Bien que la mise à niveau est prise en charge pour SQL Server 2017, une nouvelle version de Microsoft Machine Learning Server à utiliser pour les mises à niveau n’a pas été publiée.

## <a name="upgrade-an-instance"></a>Mise à niveau une instance

Le processus de mise à niveau est appelé **liaison**, car il modifie le modèle de prise en charge pour les composants SQL Server machine learning à utiliser la nouvelle stratégie de cycle de vie moderne. Toutefois, la mise à niveau ne modifie pas le modèle de prise en charge pour la base de données SQL Server.

En général, ce système de licence garantit que vos scientifiques des données utilisent toujours la dernière version de R. Pour plus d’informations sur les termes de la politique de cycle de vie moderne, consultez [Chronologie de support de Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-servicing-support).

Les effets d’une liaison d’une instance sont multiples :

+ Le modèle de prise en charge est modifié. Plutôt que sur des versions de service SQL Server, prise en charge est basée sur la nouvelle stratégie de cycle de vie moderne.
+ Les composants associés à l’instance d’apprentissage automatique seront automatiquement mis à niveau avec chaque version, dans l’étape de verrou avec la version actuelle sous la nouvelle stratégie de cycle de vie moderne. 
+ Nouveaux packages R ou Python peuvent être ajoutées. Par exemple, précédentes mises à jour à partir de Microsoft R Server ajoutés comme nouveaux packages R, [MicrosoftML](../using-the-microsoftml-package.md), [olapR](../r/how-to-create-mdx-queries-using-olapr.md), et [sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md).
+ L’instance peut ne plus être mise à jour manuellement, excepté pour ajouter de nouveaux packages.
+ Vous avez la possibilité d’ajouter des modèles préformés.

Si vous décidez ultérieurement que vous souhaitez arrêter l’instance à chaque version de la mise à niveau, vous devez **dissocier** l’instance, comme décrit dans [cette section](#bkmk_Unbind), puis désinstaller le mises à niveau d’apprentissage comme décrit dans cet article : [exécuter Microsoft R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows). Lorsque le processus est terminé, des mises à jour basées sur le serveur d’apprentissage Machine apprentissage futures n’appliquent plus à l’instance.

### <a name="bkmk_prereqs"></a>Configuration requise pour la mise à niveau

1. Identifiez les instances qui peuvent faire l’objet d’une mise à niveau.
    + SQL Server 2016 avec R Services installé
    + Au moins Service Pack 1 plus CU3

2. Obtenir **Microsoft R Server**, en téléchargeant le programme d’installation Windows distinct.

    [Comment installer R Server 9.0.1 sur Windows à l’aide du programme Windows installer autonome](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#howtoinstall)

> [!TIP]
> 
> Impossible de trouver SqlBindR.exe ? Probablement n’avez pas téléchargé R Server encore. Cet utilitaire est disponible uniquement avec le programme d’installation de Windows pour Microsoft R Server.

### <a name="bkmk_BindWizard"></a>Mise à niveau de l’aide du nouvel Assistant d’installation

1. Démarrez le programme d’installation nouveau serveur R sur l’ordinateur qui dispose de l’instance que vous souhaitez mettre à niveau.
  ![Assistant Installation de Microsoft R Server](media/r-server-installer-01.PNG)
2. Acceptez le contrat de licence pour Microsoft R Server 9.1.0, puis cliquez sur **suivant**.
3. Acceptez les conditions de licences pour les composants R open source, puis cliquez sur **suivant**.
4. Sur **sélectionner le dossier**, acceptez les valeurs par défaut ou spécifier un autre emplacement où installer les bibliothèques R. 
5. Le programme d’installation identifie toutes les instances locales qui sont des candidats à la liaison. Si aucune instance ne s’affiche, cela signifie qu’aucune instance valide a été trouvée. Vous devrez peut-être appliquer le correctif ou vérifiez si R Services a été installé.
6. Sélectionnez la case à cocher en regard de n’importe quelle instance que vous souhaitez mettre à niveau, puis cliquez sur **suivant**.
7. Le processus peut prendre un certain temps.
    
    Pendant l’installation, les bibliothèques R utilisés par SQL Server R Services sont remplacées par les bibliothèques pour Microsoft R Server 9.1.0.
    
    LaunchPad n’est pas affecté par le processus, mais les bibliothèques dans le dossier R_SERVICES seront supprimés et les propriétés pour le service seront modifiées, pour utiliser les bibliothèques dans `C:\Program Files\Microsoft\R Server\R_SERVER`.

### <a name="bkmk_BindCmd"></a>Mise à niveau de l’aide de la ligne de commande

Après l’installation de Microsoft R Server, vous pouvez exécuter simplement l’outil SqlBindR.exe à partir de la ligne de commande.

1. Ouvrez une invite de commandes en tant qu’administrateur et accédez au dossier contenant sqlbindr.exe. L’emplacement par défaut est`C:\Program Files\Microsoft\R Server\Setup`
2. Tapez la commande suivante pour afficher la liste des instances disponibles : `SqlBindR.exe /list`
  
   Notez le nom complet de l’instance tel qu’il est répertorié. Par exemple, le nom d’instance peut être `MSSQL13.MSSQLSERVER` pour l’instance par défaut, ou quelque chose comme `SERVERNAME.MYNAMEDINSTANCE`.
3. Exécutez la commande **SqlBindR.exe** avec l’argument */bind*, puis spécifiez le nom de l’instance à mettre à niveau, tel qu’il est retourné à l’étape précédente.

   Par exemple, pour mettre à niveau l’instance par défaut, tapez :`SqlBindR.exe /bind MSSQL13.MSSQLSERVER`
4. Une fois la mise à niveau terminée, redémarrez le service Launchpad associé à l’instance qui a été modifiée.


## <a name="bkmk_Unbind"></a>Rétablir ou dissocier une instance

Pour restaurer une instance de SQL Server pour utiliser les bibliothèques d’origine installés par SQL Server, vous devez effectuer une **dissocier** opération. Faire cela en réexécutant l’Assistant Installation de Microsoft R Server, ou en exécutant l’utilitaire SqlBindR à partir de la ligne de commande.

Lors de l’annulation de la liaison est terminer, les bibliothèques pour Microsoft R Server 9.1.0 sont supprimés et les bibliothèques R d’origine utilisés par SQL Server R Services sont restaurés.

Les propriétés de SQL Server Launchpad sont modifiées pour utiliser les bibliothèques R dans le dossier par défaut pour R_SERVICES, dans `C:\Program Files\Microsoft\R Server\R_SERVER`.

### <a name="unbind-using-the-wizard"></a>Supprimer la liaison à l’aide de l’Assistant

1. Télécharger le nouveau programme d’installation de Microsoft R Server 9.1.0.
2. Exécutez le programme d’installation sur l’ordinateur qui dispose de l’instance que vous souhaitez supprimer la liaison.
2. Le programme d’installation identifie les instances locales qui sont des candidats pour l’annulation de la liaison.
3. Désactivez la case à cocher en regard de l’instance que vous souhaitez revenir à la configuration de SQL Server R Services d’origine.
4. Acceptez le contrat de licence pour Microsoft R Server 9.1.0. Vous devez accepter le contrat de licence même si vous supprimez R Server.
5. Cliquez sur **Terminer**. Le processus prend un certain temps.

### <a name="unbind-using-the-command-line"></a>Supprimer la liaison à l’aide de la ligne de commande

1. Ouvrez une invite de commandes et accédez au dossier qui contient **sqlbindr.exe**, comme décrit dans la section précédente.

2. Exécutez la commande **SqlBindR.exe** avec l’argument */unbind*, puis spécifiez l’instance.

   Par exemple, la commande suivante reprend l’instance par défaut :
   
    `SqlBindR.exe /unbind MSSQL13.MSSQLSERVER`

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie spécifique de problèmes connus liés à l’aide de l’utilitaire SqlBindR.exe ou aux mises à niveau à l’aide de l’utilitaire d’installation de Microsoft R Server qui affectent les instances de SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Restauration des packages qui ont été précédemment installées

Dans l’utilitaire de mise à niveau qui a été inclus avec Microsoft R Server 9.0.1, l’utilitaire n’a pas restauré les packages d’origine ou des composants R complètement, demandant à l’utilisateur d’exécuter repair sur l’instance, s’appliquent à toutes les versions de service, puis redémarrez l’instance.

Toutefois, la dernière version de l’utilitaire de mise à niveau, de Microsoft R Server 9.1.0, restaure automatiquement les fonctions R d’origine. Par conséquent, vous ne devez pas à réinstaller les composants de R ou ré-appliquer le correctif. Toutefois, vous devrez toujours installer les packages R qui ont peut-être été ajoutées après l’installation initiale.

Si vous avez utilisé les rôles de gestion de package à installer et partager le package, cette tâche est beaucoup plus facile : vous pouvez utiliser des commandes R pour synchroniser les packages installés dans le système de fichiers à l’aide d’enregistrements dans la base de données et vice versa. Pour plus d’informations, consultez [installation et gestion des packages R](installing-and-managing-r-packages.md)

### <a name="cannot-perform-upgrade-from-901"></a>Ne peut pas effectuer de mise à niveau à partir de la version 9.0.1

Si vous avez précédemment mis à niveau une instance de SQL Server 2016 R Services à 9.0.1, lorsque vous exécutez le programme d’installation de nouveau pour Microsoft R Server 9.1.0, il affiche une liste de toutes les instances valides et puis sélectionnez précédemment liée d’instances par défaut. Si vous continuez, les instances précédemment liés sont indépendants. Par conséquent, la 9.0.1 antérieures installation est supprimée, y compris tous les packages, mais la nouvelle version de Microsoft R Server (9.1.0) n’est pas installée.

Pour résoudre ce problème, vous pouvez modifier l’installation de R Server existante comme suit :
1. Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.
2. Recherchez Microsoft R Server, puis cliquez sur **modification/modifier**.
3. Lorsque le programme d’installation démarre, sélectionnez les instances que vous souhaitez lier à 9.1.0.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>La liaison ou la séparation laisse plusieurs dossiers temporaires

La liaison et annulation de la liaison des opérations échouent parfois à nettoyer les dossiers temporaires.
Si vous trouvez des dossiers avec un nom tel que cela, vous pouvez le supprimer une fois l’installation terminée :`R_SERVICES_<guid>`

> [!NOTE]
> Veillez à attendre que l’installation est terminée. Il peut prendre beaucoup de temps à supprimer les bibliothèques R associé liés une version, puis ajoutez les nouvelles bibliothèques R. Lorsque l’opération est terminée, les dossiers temporaires seront supprimés.

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

+ [Nouveautés de R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)

+ [R Server problèmes connus](https://docs.microsoft.com/r-server/resources-known-issues)

