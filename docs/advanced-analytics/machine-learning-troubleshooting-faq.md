---
title: "Résolution des problèmes et Forum aux questions pour l’apprentissage dans SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: 6e45e8dc4df1404833fddd9000eb40cad6e5299f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---

# <a name="troubleshoot-machine-learning"></a>Résoudre les problèmes d’apprentissage

Cet article fournit des informations de dépannage relatives à l’installation et configuration des fonctionnalités d’apprentissage machine dans SQL Server. Ces informations incluent des liens vers les guides d’installation, les problèmes connus et les notes de publication. Autres articles lié à partir de cet article fournit des conseils sur l’optimisation des performances pour les solutions d’apprentissage machine dans SQL Server.

Utilisez cette page comme point de départ pour la recherche de problèmes connus, les questions de configuration courantes et les procédures de dépannage.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage Services (R et Python)

## <a name="known-issues"></a>Problèmes connus

Les articles suivants de la liste des problèmes connus avec la version actuelle ou décrivent les problèmes avec les versions précédentes :

+ [Problèmes connus pour R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Notes de publication de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="troubleshooting-prerequisites"></a>Résolution des problèmes de configuration requise

Si vous avez rencontré une erreur, ou que vous devez comprendre un problème dans votre environnement, il est important de collecter des informations connexes systématiquement. Ces informations incluent la version, l’Édition, le contexte de sécurité et le contexte d’exécution.

L’article suivant fournit une liste d’informations qui facilite le dépannage élaborés d’auto-assistance ou d’une demande de support technique.

+ [Collecte de données pour la résolution des problèmes de l’apprentissage](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guides d’installation et configuration

Si vous n’avez pas configuré apprentissage avec SQL Server, ou si vous souhaitez ajouter la fonctionnalité, commencez ici :

+ [Configurer les Services de R ou Machine Learning Services avec R](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)
+ [Configurer les Services d’apprentissage Machine avec Python](../advanced-analytics/python/setup-python-machine-learning-services.md)
+ [Programme d’installation Forum aux questions](../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [SqlBindR permet de mettre à niveau une instance de R services](../advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

Les articles suivants décrivent les étapes supplémentaires requises pour le programme d’installation hors connexion des fonctionnalités d’apprentissage machine dans SQL Server :

+ [Installation sans assistance de R Services](../advanced-analytics/r/unattended-installs-of-sql-server-r-services.md) 
+ [Installation sans assistance de Machine Learning Services avec Python](../advanced-analytics/python/unattended-installs-of-sql-server-python-services.md)

Si vous avez besoin installer les fonctionnalités sur un ordinateur disposant d’aucune connexion Internet d’apprentissage automatique, utilisez les liens dans cet article pour télécharger les composants R et Python avant de lancer le programme d’installation :

+ [Installation des composants d’apprentissage machine sans accès à Internet](../advanced-analytics/r/installing-ml-components-without-internet-access.md)

### <a name="configuration"></a>Configuration

Les articles suivants contiennent des informations sur les valeurs par défaut et comment personnaliser la configuration pour l’apprentissage sur une instance :

+ [Modifier le pool de comptes d’utilisateur pour SQL Server R Services](../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Configurer et gérer les extensions d’analytique avancée](../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Comment créer un pool de ressources](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimisation pour les charges de travail R](r/operationalizing-your-r-code.md)

## <a name="related-tools-and-services"></a>Services et les outils connexes

+ [Configurer Microsoft Machine Learning serveur autonome](../advanced-analytics/r/create-a-standalone-r-server.md)
+ [Configurer le serveur R sur une machine virtuelle Azure](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
+ [Installer R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
+ [Obtenir les outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/)

