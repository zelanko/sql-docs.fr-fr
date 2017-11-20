---
title: "Ajouter une SSIS avec montée en puissance travail avec montée en puissance parallèle Manager | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b769236330941a107865a0b133961bce5bf6b85b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Ajouter une montée en charge travail avec montée en puissance parallèle Manager

Integration Services échelle Out Manager diminue considérablement la complexité pour ajouter la montée en puissance des processus de travail à votre environnement de monter en charge. 

Les étapes ci-dessous permettent d’ajouter un montée en puissance des processus de travail à votre topologie de monter en charge :

## <a name="1-install-scale-out-worker"></a>1. Installer la montée en charge de travail
Dans l’Assistant installation de SQL Server, sélectionnez les Services d’intégration et de montée en puissance des processus de travail sur le **sélection des fonctionnalités** page. 
![Sélection de la fonctionnalité Worker](media/feature-select-worker.PNG)

Sur le **Configuration Integration Services échelle Out - nœud de travail** page, vous pouvez simplement cliquer sur « Suivant » pour ignorer la configuration ici et utilisez **échelle Out Manager** pour effectuer la configuration après l’installation.

Terminez l’Assistant installation.

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2. Ouvrez le pare-feu sur ordinateur échelle Out principal
Ouvrir le port spécifié pendant l’installation de la mise à l’échelle des principale (8391, par défaut) et le port du serveur SQL Server (1433 par défaut), à l’aide de pare-feu Windows sur l’ordinateur de l’échelle des principales.

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3. Ajouter avec montée en charge le Gestionnaire de montée en charge de travail
Exécutez SQL Server Management Studio en tant qu’administrateur et connectez-vous à l’instance de SQL Server de l’échelle des principales.

Avec le bouton droit **SSISDB** dans l’Explorateur d’objets et sélectionnez **gérer les monter en charge...** . 

![Gérer la montée en puissance parallèle](media/manage-scale-out.PNG)

Dans la liste dépilé des **échelle Out Manager**, basculez vers **Gestionnaire de processus de travail**. Cliquez sur « + » bouton et suivez les instructions dans la boîte de dialogue se connecter le processus de travail. Pour plus d’informations, consultez [échelle Out Manager](integration-services-ssis-scale-out-manager.md).

