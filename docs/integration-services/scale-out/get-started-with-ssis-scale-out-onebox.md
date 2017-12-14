---
title: "Bien démarrer avec SSIS Scale Out sur un seul ordinateur| Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8514cd548b003a39bf198b83b6b80d775a55384b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Bien démarrer avec Integration Services (SSIS) Scale Out sur un seul ordinateur
Cette section explique comment configurer Integration Services Scale Out dans un environnement à un seul ordinateur avec les paramètres par défaut.

## <a name="1-install-sql-server-features"></a>1. Installer les fonctionnalités SQL Server
Dans l’Assistant Installation de SQL Server, sélectionnez Services Moteur de base de données, Integration Services, Scale Out Master et Scale Out Worker dans la page **Sélection de fonctionnalités**.

![Sélection de fonctionnalités - Ordinateur unique 1](media/feature-select-onebox1.PNG)

![Sélection de fonctionnalités - Ordinateur unique 2](media/feature-select-onebox2.PNG)

Dans la page **Configuration du serveur**, cliquez simplement sur « Suivant » pour utiliser des comptes de service et des types de démarrage par défaut.

Dans la page **Configuration du moteur de base de données**, sélectionnez **Mode mixte**, puis cliquez sur le bouton **Ajouter l’utilisateur actuel**. 

![Configuration du moteur](media/engine-config.PNG)

Dans les pages **Configuration d’Integration Services Scale Out - Nœud master** et **Configuration d’Integration Services Scale Out - Nœud worker**, cliquez simplement sur « Suivant » pour appliquer les paramètres par défaut de port et de certificats.

Terminez l’Assistant Installation de SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Installer SQL Server Management Studio

[Téléchargez](../../ssms/download-sql-server-management-studio-ssms.md) SQL Server Management Studio et installez-le.

## <a name="3-enable-scale-out"></a>3. Activer Scale Out
Ouvrez SSMS et connectez-vous à l’instance locale de SQL Server.
Cliquez avec le bouton droit sur **Catalogues Integration Services** dans l’Explorateur d’objets, puis sélectionnez **Créer un catalogue**.

Dans la boîte de dialogue **Créer un catalogue**, **Activer ce serveur comme SSIS Scale Out Master** est sélectionné par défaut. Créez simplement le catalogue comme d’habitude. 

## <a name="4-enable-scale-out-worker"></a>4. Activer Scale Out Worker
Dans SSMS, cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Gérer Scale Out**. ![Gérer Scale Out](media/manage-scale-out.PNG)

Integration Services Scale Out Manager apparaît. Vous pouvez l’utiliser pour gérer Scale Out. Pour plus d’informations, consultez [Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md).

Pour activer le Scale Out Worker, passez au **Gestionnaire de workers**, puis sélectionnez le Worker à activer. Le Worker est désactivé initialement. Cliquez sur **Activer le Worker** pour l’activer.

## <a name="5-run-packages-in-scale-out"></a>5. Exécuter des packages dans Scale Out
Maintenant, vous êtes prêt à exécuter des packages SSIS dans Scale Out. Consultez [Exécuter des packages dans Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md).


Pour ajouter des Scale Out Workers, consultez [Ajouter un Scale Out Worker avec Scale Out Manager](add-scale-out-worker.md).
