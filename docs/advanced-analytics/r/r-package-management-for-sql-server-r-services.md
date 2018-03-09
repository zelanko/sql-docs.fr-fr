---
title: "Installation et gestion des packages d’apprentissage machine dans SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 02/19/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 98c14b05-750e-44f9-8531-1298bf51e8d2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 0fd96240581203d9f948372dfbe98cac80a3b906
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="installing-and-managing-machine-learning-packages-in-sql-server"></a>Installation et gestion des packages d’apprentissage machine dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment vous pouvez installer de nouveaux packages R ou Python dans SQL Server 2017 et dans SQL Server 2016. Elle décrit également les limitations sur les packages que vous pouvez installer sur SQL Server.

## <a name="overview-of-package-management-methods-and-requirements"></a>Vue d’ensemble des méthodes de gestion de package et les exigences

Contrairement à un développement R ou Python classique, les packages utilisés par SQL Server doivent être installés dans un dossier sous contrôle de l’administration. Il existe de nombreux avantages à la conservation des packages dans un emplacement unique :

+ L’administrateur du serveur peut surveiller l’ajout de nouveaux fichiers de bibliothèques sur le serveur et contrôler la croissance des fichiers utilisés par des bibliothèques de package. 
+ Packages peuvent être plus facilement partagés par plusieurs utilisateurs de base de données, par opposition à l’installation de plusieurs copies du même package dans les bibliothèques de l’utilisateur.
+ Seuls les packages sécurisées, approuvés peuvent être installés pour protéger le serveur et ses opérations.

Toutefois, ces restrictions nécessairement certaines modifications dans la manière dont les analystes et les chercheurs de données fonctionnent :

+ En règle générale, un accès administratif au serveur est requis. Dans SQL Server 2017, l’administrateur de base de données pouvez utiliser des rôles pour accorder à certains utilisateurs la possibilité d’installer des packages pour une utilisation privée, mais l’administrateur a toujours activer cette fonctionnalité.
+ Nombre de serveurs n’ont pas accès à Internet. Installation des packages à ces ordinateurs nécessite une préparation supplémentaire.
+ Les packages sont installés dans la bibliothèque d’instance. Les packages ne peuvent pas être partagés entre les instances.
+ Les utilisateurs ne peuvent pas exécuter n’importe quel package a été installé dans une bibliothèque de l’utilisateur.

## <a name="package-installation-guides-for-r-or-python"></a>Guides d’installation de package de R ou Python

Consultez les articles suivants pour obtenir des instructions détaillées sur la façon d’installer de nouveaux packages R ou Python. 

### <a name="install-new-r-packages"></a>Installation de nouveaux packages R

+ [Installer des packages R supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md)

    Vous pouvez installer des packages R sur SQL Server 2016 ou 2017 en tant qu’administrateur, à l’aide des outils R.

    Vous pouvez également installer des packages R à partir d’un client de R distant où R Server 9.0.2 ou version ultérieure est installé.

    Vous pouvez également installer des packages R dans SQL Server 2017 est à l’aide des instructions DDL.

### <a name="install-new-python-packages"></a>Installation de nouveaux packages Python

+ [Installer de nouveaux packages Python sur SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="prerequisites"></a>Configuration requise

Avant de pouvoir télécharger ou installer un nouveau package, passez en revue la configuration requise :

+ Assurez-vous qu’il existe une version Windows du package : [mise en route de la version de package approprié et le format](#packageVersion)

+ Identifier toutes les dépendances de package et déterminer leur compatibilité avec l’environnement SQL Server.

+ Vérifiez la version de R ou la compatibilité de versions de Python. Le package doit être compatible avec la version de R ou Python est en cours d’exécution dans SQL Server.

+ Autorisations. Déterminez si vous disposez des droits pour installer le package. Pour installer à la bibliothèque de l’instance, l’accès administratif à l’ordinateur exécutant SQL Server est requis. Si vous n’avez pas un accès administratif à l’ordinateur SQL Server, recherchez un administrateur de base de données à l’aide sur l’installation du package.

    Dans SQL Server 2017, vous pouvez installer des packages R à partir d’un client distant, si la gestion des packages a été activée sur le serveur et vous êtes le propriétaire de la base de données ou un membre d’un rôle de gestion du package.

+ Tenez compte des risques et avantages de l’installation d’un package particulier dans l’environnement SQL Server. Vérifiez si le package (ou tous les packages dont il a besoin) contient des fonctionnalités qui seraient bloquées par SQL Server ou par la stratégie. De nombreux packages R et Python sont très pour un environnement SQL Server renforcé. Des problèmes peuvent inclure :

    - Packages qui accèdent au réseau
    - Packages qui nécessitent Java ou autres infrastructures généralement pas utilisés dans un environnement SQL Server
    - Packages qui nécessitent un accès de système de fichier avec élévation de privilèges
    - Package est utilisé pour le développement web ou d’autres tâches qui ne bénéficient en exécutant à l’intérieur de SQL Server.

## <a name="installation-on-servers-with-no-internet-access"></a>Installation sur des serveurs sans accès à Internet

En général, les serveurs qui hébergent les bases de données de production ne permettent pas de connexion à Internet. L’installation de nouveaux packages R ou Python dans de tels environnements nécessite que vous préparez à l’avance de tous les packages et leurs dépendances et copiez les fichiers dans un dossier sur le serveur pour une utilisation dans l’installation.

1. Identifier toutes les dépendances du package. 
2. Vérifiez si tous les packages requis sont déjà installés sur le serveur. Si le package est installé, vérifiez que la version est correcte.
3. Téléchargez le package et toutes les dépendances sur un ordinateur distinct.
4. Déplacez les fichiers dans un dossier accessible par le serveur.
5. Exécuter une instruction DDL ou une commande d’installation pris en charge pour installer le package dans la bibliothèque de l’instance.

Identifier toutes les dépendances peut être complexe. Pour R, nous vous recommandons d’utiliser [miniCRAN](create-a-local-package-repository-using-minicran.md) pour préparer un référentiel de packages en mode hors connexion.

Pour Python, vous devez de la même façon préparer toutes les dépendances et les enregistrer localement. Veillez à utiliser des binaires compatibles avec Windows et utilisez le format WHL.
