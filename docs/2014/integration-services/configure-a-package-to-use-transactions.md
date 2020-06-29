---
title: Configurer un package pour utiliser des transactions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25c111830727c7ca75357a06a0eb40ebd00aee9f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434856"
---
# <a name="configure-a-package-to-use-transactions"></a>Configurer un package pour l'utilisation de transactions
  Lorsque vous configurez un package pour l'utilisation de transactions, vous avez le choix entre deux options :  
  
-   Avoir une transaction unique pour le package. Dans ce cas, le package *lance* lui-même cette transaction, alors que les tâches et les conteneurs individuels dans le package participent à cette transaction unique.  
  
-   Avoir plusieurs transactions dans le package. Dans ce cas, le package prend en charge des transactions, mais les tâches et les conteneurs individuels dans le package lancent en réalité les transactions.  
  
 Les procédures ci-dessous montrent comment configurer ces deux options.  
  
## <a name="configuring-a-single-transaction"></a>Configuration d'une transaction unique  
 Dans cette option, le package lui-même lance une transaction unique. Vous configurez le package pour lancer cette transaction en affectant à la propriété TransactionOption du package la valeur `Required` .  
  
 Ensuite, vous inscrivez des tâches et des conteneurs spécifiques dans cette transaction unique. Pour inscrire une tâche ou un conteneur dans une transaction, vous affectez à la propriété TransactionOption de cette tâche ou de ce conteneur la valeur `Supported` .  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a>Pour configurer un package de façon à utiliser une transaction unique  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package à configurer pour utiliser une transaction.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de la surface de dessin du flux de contrôle, puis cliquez sur **Propriétés**.  
  
5.  Dans la fenêtre **Propriétés** , affectez à la propriété TransactionOption la valeur `Required` .  
  
6.  Sur la surface de dessin de l’onglet **Flux de contrôle** , cliquez avec le bouton droit sur la tâche ou le conteneur que vous souhaitez inscrire dans la transaction, puis cliquez sur **Propriétés**.  
  
7.  Dans la fenêtre **Propriétés** , affectez à la propriété TransactionOption la valeur `Supported` .  
  
    > [!NOTE]  
    >  Pour inscrire une connexion dans une transaction, inscrivez les tâches qui utilisent la connexion dans la transaction. Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
8.  Répétez les étapes 6 et 7 pour chaque tâche et conteneur que vous voulez inscrire dans la transaction.  
  
## <a name="configuring-multiple-transactions"></a>Configuration de plusieurs transactions  
 Dans cette option, le package lui-même prend en charge les transactions mais ne démarre pas une transaction. Vous configurez le package pour prendre en charge les transactions en affectant à la propriété TransactionOption du package la valeur `Supported` .  
  
 Ensuite, vous configurez les tâches et les conteneurs de votre choix au sein du package pour lancer des transactions ou y participer. Pour configurer une tâche ou un conteneur pour lancer une transaction, vous affectez à la propriété TransactionOption de cette tâche ou de ce conteneur la valeur `Required` .  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a>Pour configurer un package de façon à utiliser plusieurs transactions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package que vous voulez configurer de façon à utiliser des transactions.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de la surface de dessin du flux de contrôle, puis cliquez sur **Propriétés**.  
  
5.  Dans la fenêtre **Propriétés** , affectez à la propriété TransactionOption la valeur `Supported` .  
  
    > [!NOTE]  
    >  Le package prend en charge les transactions, mais les transactions sont démarrées par la tâche ou des conteneurs dans le package.  
  
6.  Sur la surface de dessin de l’onglet **Flux de contrôle** , cliquez avec le bouton droit sur la tâche ou le conteneur du package pour lequel vous souhaitez commencer une transaction, puis cliquez sur **Propriétés**.  
  
7.  Dans la fenêtre **Propriétés** , affectez à la propriété TransactionOption la valeur `Required` .  
  
8.  Si une transaction est commencée par un conteneur, cliquez avec le bouton droit sur la tâche ou le conteneur que vous souhaitez inscrire dans la transaction, puis cliquez sur **Propriétés**.  
  
9. Dans la fenêtre **Propriétés** , affectez à la propriété TransactionOption la valeur `Supported` .  
  
    > [!NOTE]  
    >  Pour inscrire une connexion dans une transaction, inscrivez les tâches qui utilisent la connexion dans la transaction. Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md).  
  
10. Répétez les étapes 6 à 9 pour chaque tâche et conteneur qui démarre une transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions Integration Services](integration-services-transactions.md)  
  
  
