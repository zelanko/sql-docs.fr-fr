---
title: Ajouter un SSIS Scale Out Worker avec Scale Out Manager | Microsoft Docs
description: Cet article explique comment ajouter un Scale Out Worker SSIS à un environnement Scale Out avec Scale Out Manager.
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: b028c143cdc635792f9f1bd01cbdadf9e8f98454
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642987"
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Ajouter un Scale Out Worker avec Scale Out Manager

Integration Services Scale Out Manager simplifie l’ajout d’un Scale Out Worker à votre environnement Scale Out existant. 

Suivez les étapes ci-dessous pour ajouter un Scale Out Worker à votre topologie Scale Out :

## <a name="1-install-scale-out-worker"></a>1. Installer Scale Out Worker
Dans l’Assistant Installation de SQL Server, sélectionnez Integration Services et Scale Out Worker dans la page **Sélection de fonctionnalités**. 
![Sélection de la fonctionnalité Worker](media/feature-select-worker.PNG)

Dans la page **Configuration d’Integration Services Scale Out - Nœud Worker**, vous pouvez cliquer sur **Suivant** pour ignorer la configuration à ce stade et utiliser **Scale Out Manager** pour effectuer la configuration après l’installation.

Terminez l’Assistant Installation.

## <a name="2-open-the-firewall-on-the-scale-out-master-computer"></a>2. Ouvrir le pare-feu sur l’ordinateur Scale Out Master
Ouvrez le port spécifié pendant l’installation de Scale Out Master (8391, par défaut) et le port pour SQL Server (1433, par défaut) dans le Pare-feu Windows sur l’ordinateur Scale Out Master.

## <a name="3-add-a-scale-out-worker-with-scale-out-manager"></a>3. Ajouter un Scale Out Worker avec Scale Out Manager
Exécutez SQL Server Management Studio en tant qu’administrateur et connectez-vous à l’instance SQL Server de Scale Out Master.

Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **SSISDB** et sélectionnez **Gérer Scale Out**. 

![Gérer Scale Out](media/manage-scale-out.PNG)

Dans la boîte de dialogue **Scale Out Manager**, basculez vers **Gestionnaire de workers**. Sélectionnez **+** et suivez les instructions de la boîte de dialogue **Connect Worker** (Connecter le nœud Worker). 

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations, consultez [Scale Out Manager](integration-services-ssis-scale-out-manager.md).
