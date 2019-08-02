---
title: Résolution des problèmes et FAQ pour Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1573c260c3d34ba3f733316fbae2672b2f9adfb1
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715156"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Résoudre les problèmes de Machine Learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Utilisez cette page comme point de départ pour l’utilisation de problèmes connus.

## <a name="known-issues"></a>Problèmes connus

Les articles suivants décrivent les problèmes connus avec les versions actuelles et précédentes:

+ [Problèmes connus pour R services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Notes de publication de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Comment collecter des informations système

Si vous avez rencontré une erreur ou si vous devez comprendre un problème dans votre environnement, il est important de collecter systématiquement les informations associées. L’article suivant fournit une liste d’informations qui facilitent le dépannage de l’auto-assistance ou une demande de support technique.

+ [Collecte de données pour la résolution des problèmes de Machine Learning](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guides d’installation et de configuration

Commencez ici si vous n’avez pas configuré Machine Learning avec SQL Server ou si vous souhaitez ajouter la fonctionnalité:

+ [Installer SQL Server Machine Learning Services (dans la base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Installer SQL Server Machine Learning Server (autonome)](install/sql-machine-learning-standalone-windows-install.md)
+ [Configuration de l’invite de commandes](install/sql-ml-component-commandline-install.md)
+ [Configuration en mode hors connexion (sans Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Configuration

Les articles suivants contiennent des informations sur les valeurs par défaut et expliquent comment personnaliser la configuration de Machine Learning sur une instance:

+ [Mettre à l’échelle l’exécution simultanée de scripts externes dans SQL Server Machine Learning Services](administration/modify-user-account-pool.md)   
+ [Configurer et gérer les extensions analytiques avancées](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Comment créer un pool de ressources](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimisation des charges de travail R](r/operationalizing-your-r-code.md)
