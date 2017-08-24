---
title: "Commencer avec une échelle SSIS sur un seul ordinateur | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7175c63be4c0e15e50f2020f75d283ac0e3dfdbf
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Prise en main Integration Services (SSIS) l’élargissement sur un seul ordinateur
Cette section fournit les instructions de configuration d’Integration Services monter en charge dans un environnement d’une case avec les paramètres par défaut.

## <a name="1-install-sql-server-features"></a>1. Installer les fonctionnalités de SQL Server
Dans l’Assistant installation de SQL Server, sélectionnez Services moteur de base de données, Integration Services, mise à l’échelle des Master et montée en puissance des processus de travail sur le **sélection des fonctionnalités** page.

![Unifiée de sélection de fonctionnalité 1](media/feature-select-onebox1.PNG)

![Fonctionnalité unifiée sélectionnez 2](media/feature-select-onebox2.PNG)

Sur le **Configuration du serveur** , cliquez simplement sur « Suivant » pour utiliser des comptes de service par défaut et les types de démarrage.

Sur le **Configuration du moteur de base de données** page, sélectionnez «**en Mode mixte**« et cliquez sur »**ajouter l’utilisateur actuel**» bouton. 

![Configuration du moteur](media/engine-config.PNG)

Un seul le **Configuration Integration Services échelle Out - nœud maître** et **Configuration Integration Services échelle Out - nœud de travail** pages, cliquez simplement sur « Suivant » pour appliquer les paramètres par défaut du port et des certificats.

Terminez l’Assistant d’installation de SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Installer SQL Server Management Studio

[Télécharger](../../ssms/download-sql-server-management-studio-ssms.md) SQL Server Management Studio et l’installer.

## <a name="3-enable-scale-out"></a>3. Activer la montée en puissance parallèle
Ouvrez SSMS et connectez-vous à l’instance locale de Sql Server.
Avec le bouton droit **catalogues Integration Services** dans l’Explorateur d’objets et sélectionnez **créer un catalogue**.

Dans le **créer un catalogue** boîte de dialogue, **activer ce serveur en tant que maître de montée SSIS** est sélectionnée par défaut. Créez simplement le catalogue comme d’habitude. 

## <a name="4-enable-scale-out-worker"></a>4. Activer la montée en charge de travail
Dans SSMS, cliquez sur **SSISDB** et sélectionnez **gérer les monter en charge...** . 
![Gérer la montée en puissance parallèle](media/manage-scale-out.PNG)

L’intégration échelle Out Gestionnaire des Services s’affiche. Monter en charge, vous pouvez gérer avec lui. Pour plus d’informations, consultez [Integration Services échelle Out Manager](integration-services-ssis-scale-out-manager.md).

Pour activer le montée en puissance des processus de travail, passez à **travail Manager** et sélectionnez le processus de travail que vous souhaitez activer. Le processus de travail est désactivé initialement. Cliquez sur **activer un travail** pour l’activer.

## <a name="5-run-packages-in-scale-out"></a>5. Exécuter des packages dans Scale Out
Maintenant, vous êtes prêt à exécuter des packages SSIS dans monter en charge. Consultez [exécutent des Packages Integration Services (SSIS) montée en puissance parallèle](run-packages-in-integration-services-ssis-scale-out.md).


Pour ajouter davantage de traitements de monter en charge, consultez [ajouter un montée en puissance des processus de travail avec montée en puissance Out Manager](add-scale-out-worker.md).
