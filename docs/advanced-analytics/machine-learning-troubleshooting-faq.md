---
title: "Résolution des problèmes et Forum aux questions pour l’apprentissage dans SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 5b9a5c6497781ef67d9d2ef9b9032a4d9ee250e5
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2018
---
# <a name="troubleshoot-machine-learning"></a>Résoudre les problèmes d’apprentissage
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fournit des liens de dépannage aux guides d’installation, les problèmes connus et les notes de publication. Autres articles lié à partir de cet article fournit des conseils sur l’optimisation des performances pour les solutions d’apprentissage machine dans SQL Server.

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

+ [Installer SQL Server 2017 Machine Learning Services (de-de base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Installer SQL Server 2017 Machine Learning Server (autonome)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installer SQL Server 2016 R Services (de-de base de données)](install/sql-r-services-windows-install.md)
+ [Installer SQL Server 2016R Server (autonome)](install/sql-r-standalone-windows-install.md)
+ [Programme d’installation de ligne de commande](install/sql-ml-component-commandline-install.md)
+ [Programme d’installation en mode hors connexion (aucune internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Configuration

Les articles suivants contiennent des informations sur les valeurs par défaut et comment personnaliser la configuration pour l’apprentissage sur une instance :

+ [Modifier le pool de comptes d’utilisateur pour SQL Server R Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Configurer et gérer les extensions d’analytique avancée](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Comment créer un pool de ressources](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimisation pour les charges de travail R](r/operationalizing-your-r-code.md)
