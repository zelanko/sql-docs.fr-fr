---
title: Utiliser les relations de valeur dans un domaine composite
ms.date: 11/22/2011
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 03f90fb4e97ac7671ba4f09ff5dc6ad32bfcf84b
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812512"
---
# <a name="use-value-relations-in-a-composite-domain"></a>Utiliser les relations de valeur dans un domaine composite

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Cette rubrique décrit comment afficher les combinaisons de valeurs trouvées pour le domaine composite pendant le processus de découverte des connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Cette page affiche le nombre d'occurrences des combinaisons de valeur. La gestion de valeur n'est pas prise en charge pour les domaines composites, vous ne pouvez donc pas exécuter d'opérations sur ces valeurs.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Pour afficher les relations de valeur, vous devez avoir créé et ouvert un domaine composite.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour afficher les relations de valeur dans un domaine composite.  
  
##  <a name="view-value-relations"></a><a name="Use"></a>Afficher les relations de valeur  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez ou créez une base de connaissances. Sélectionnez **Gestion de l'arborescence du domaine** comme activité, puis cliquez sur **Ouvrir** ou **Créer**. Pour plus d’informations, consultez [Créer une base de connaissances](../data-quality-services/create-a-knowledge-base.md) ou [Ouvrir une base de connaissances](../data-quality-services/open-a-knowledge-base.md).  
  
3.  Dans **Liste des domaines** de la page **Gestion de l'arborescence du domaine** , sélectionnez le domaine composite pour lequel vous souhaitez créer une règle de domaine, ou créez un nouveau domaine composite. Si vous devez créer un domaine, consultez [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md).  
  
4.  Cliquez sur l'onglet **Relations de valeurs** .  
  
5.  Affichez les fréquences affichées pour chaque combinaison de valeurs.  
  
    > [!NOTE]  
    >  La table **Valeur** affiche chaque combinaison de valeurs qui existe dans le domaine composite. Chaque valeur est affichée dans le domaine simple auquel elle s'applique. Le tri par défaut de la table de relations de valeur se fait sur la fréquence, mais vous pouvez cliquer sur une autre colonne pour trier sur cette colonne. Seules les valeurs ayant une fréquence supérieure ou égale à 20 sont affichées.  
  
6.  Vous ne pouvez pas modifier l'une des valeurs de la table. Si vous avez exécuté d'autres opérations, cliquez sur **Terminer** pour terminer l'activité de gestion de domaine. Sinon, cliquez sur **Annuler**.  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a>Suivi : après l’affichage des relations de valeur  
 Après avoir affiché les relations de valeur, vous pouvez effectuer d'autres tâches de gestion des domaines sur le domaine, effectuer une découverte des connaissances pour ajouter des connaissances au domaine ou ajouter une stratégie de correspondance au domaine. Pour plus d’informations, consultez [Effectuer une découverte des connaissances](../data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../data-quality-services/managing-a-domain.md) ou [Créer une stratégie de correspondance](../data-quality-services/create-a-matching-policy.md).  
  
  
