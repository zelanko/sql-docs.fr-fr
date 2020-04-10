---
title: Dépannage
description: Fournit un point de départ pour traiter les problèmes connus.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 16f85f78caed45119003d420636a90d226df127d
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81118182"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Résoudre les problèmes de machine learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Utilisez cet article comme point de départ pour traiter les problèmes connus.

## <a name="known-issues"></a>Problèmes connus

Les articles suivants décrivent les problèmes connus liés aux versions actuelles et précédentes :

+ [Problèmes connus pour R Services](../machine-learning/known-issues-for-sql-server-machine-learning-services.md)
+ [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Notes de publication de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Comment collecter des informations système

Si vous avez rencontré une erreur ou que vous devez comprendre un problème dans votre environnement, il est important de collecter systématiquement les informations associées. L’article suivant fournit une liste d’informations qui facilitent le dépannage autonome ou la formulation d’une demande de support technique.

+ [Collecte de données pour la résolution des problèmes de machine learning](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guides d’installation et de configuration

Commencez ici si vous n’avez pas configuré le machine learning avec SQL Server ou si vous souhaitez ajouter la fonctionnalité :

+ [Installer SQL Server Machine Learning Services (dans la base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Installer SQL Server Machine Learning Server (autonome)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installation à partir de l’invite de commandes](install/sql-ml-component-commandline-install.md)
+ [Configuration en mode hors connexion (sans Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Configuration

Les articles suivants contiennent des informations sur les valeurs par défaut et expliquent comment personnaliser la configuration du machine learning sur une instance :

+ [Mettre à l’échelle l’exécution simultanée de scripts externes dans SQL Server Machine Learning Services](administration/scale-concurrent-execution-external-scripts.md)   
+ [Guide pratique pour créer un pool de ressources](administration/create-external-resource-pool.md)
+ [Optimisation des charges de travail R](r/operationalizing-your-r-code.md)
